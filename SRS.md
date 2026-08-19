## bước 1:- đọc và phân tích yêu cầu: hiểuu về bussiness contesxt và bussiness problem
       - trả lời câu hỏi: khách hàng muốn giải quyết vána đè gì
       - vì sao k thể đáp ứng, ai sử dụng ht này,
       - giá trị sau khi tạo ra

**1. Khách hàng muốn giải quyết vấn đề gì?**
Công ty ABC muốn xây dựng **CAB System** để tự động hóa và quản lý tập trung toàn bộ quy trình đặt xe: **đặt xe → tìm tài xế → thực hiện chuyến → tính cước → thanh toán → đánh giá**. 

**2. Vì sao hệ thống hiện tại không thể đáp ứng?**
* Phân công tài xế chủ yếu **thủ công**.
* Khách hàng khó **theo dõi trạng thái chuyến đi**.
* Thông tin **thanh toán chưa được quản lý tập trung**.
* Khó **mở rộng hệ thống** khi số lượng khách hàng và tài xế tăng. 

**3. Ai sử dụng hệ thống?**
* **Customer:** đặt xe, theo dõi chuyến, thanh toán, đánh giá.
* **Driver:** nhận/từ chối chuyến, cập nhật vị trí và trạng thái chuyến.
* **Operation Staff/Admin:** quản lý khách hàng, tài xế, phương tiện, chuyến đi và báo cáo. 

**4. Giá trị sau khi tạo ra hệ thống?**
* Tự động hóa quy trình đặt và điều phối xe.
* Cải thiện trải nghiệm Customer và Driver.
* Quản lý dữ liệu và hoạt động tập trung.
* Giảm khó khăn cho bộ phận vận hành.
* Có khả năng **scale và mở rộng tính năng** trong tương lai.

## bước 2: Xác định stakeholder trong dự án này
- lập bảng cột đầu stakeholder nào, cột 2 vai trò là gì
- vẽ ma trận stakeholder, cho biết mức độ ảnh hưởng của các vai trò trong hệ thống

Dựa trên yêu cầu của CAB System, các stakeholder chính gồm: 
| Stakeholder                 | Vai trò                                                               |
| --------------------------- | --------------------------------------------------------------------- |
| **Ban giám đốc ABC**        | Đưa ra mục tiêu, yêu cầu kinh doanh và định hướng phát triển hệ thống |
| **Customer**                | Đặt xe, theo dõi chuyến, thanh toán và đánh giá tài xế                |
| **Driver**                  | Nhận/từ chối chuyến, thực hiện chuyến và cập nhật trạng thái/vị trí   |
| **Operation Staff / Admin** | Quản lý khách hàng, tài xế, phương tiện, chuyến đi và xử lý sự cố     |
| **Business Analyst (BA)**   | Thu thập, phân tích và làm rõ yêu cầu với các bên liên quan           |
| **Development Team**        | Thiết kế, phát triển, tích hợp và triển khai CAB System               |
| **Payment Provider**        | Cung cấp dịch vụ xử lý thanh toán điện tử                             |
| **Notification Provider**   | Cung cấp kênh gửi thông báo cho Customer và Driver                    |

### Stakeholder Matrix

Có thể phân loại theo **Power (mức độ ảnh hưởng/quyền lực)** và **Interest (mức độ quan tâm đến hệ thống)**:

```text
                     POWER / INFLUENCE
                           HIGH
                            ↑
                            │
       KEEP SATISFIED       │        MANAGE CLOSELY
                            │
    Payment Provider        │    Ban giám đốc ABC
                            │    Operation Staff/Admin
                            │    BA
                            │    Development Team
                            │
LOW INTEREST ───────────────┼──────────────────── HIGH INTEREST
                            │
       MONITOR              │        KEEP INFORMED
                            │
 Notification Provider      │    Customer
                            │    Driver
                            │
                            ↓
                           LOW
```

### Mức độ ảnh hưởng

| Stakeholder               | Mức độ ảnh hưởng  | Lý do chính                                                        |
| ------------------------- | -----------------  | ------------------------------------------------------------------ |
| **Ban giám đốc ABC**      | 🔴 Cao            | Quyết định mục tiêu, phạm vi và yêu cầu kinh doanh                 |
| **Operation Staff/Admin** | 🔴 Cao            | Trực tiếp vận hành và quản lý hệ thống                             |
  | **BA**                  | 🔴 Cao            | Làm rõ requirement và kết nối stakeholder với Development Team     |
| **Development Team**      | 🔴 Cao            | Quyết định và triển khai giải pháp kỹ thuật                        |
| **Payment Provider**      | 🟠 Trung bình–Cao | Ảnh hưởng trực tiếp đến chức năng thanh toán điện tử               |
| **Customer**              | 🟠 Trung bình     | Người sử dụng chính, yêu cầu ảnh hưởng lớn đến chức năng đặt xe    |
| **Driver**                | 🟠 Trung bình     | Người trực tiếp tham gia Driver Matching và Trip                   |
| **Notification Provider** | 🟡 Trung bình     | Ảnh hưởng đến Notification nhưng không quyết định toàn bộ hệ thống |

## Bước 3:Tìm business goal
Business Goal là mục tiêu kinh doanh mà doanh nghiệp muốn đạt được khi xây dựng hệ thống.

| Business Goal                                | Mục tiêu cụ thể                                                                                   |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **BG1. Tự động hóa đặt xe**                  | Tự động tiếp nhận yêu cầu và tìm/phân công tài xế phù hợp thay cho việc phân công thủ công.       |
| **BG2. Nâng cao trải nghiệm khách hàng**     | Cho phép khách hàng đặt xe, theo dõi trạng thái, vị trí tài xế, thanh toán và đánh giá chuyến đi. |
| **BG3. Nâng cao hiệu quả vận hành**          | Giúp nhân viên quản lý tập trung khách hàng, tài xế, phương tiện và chuyến đi.                    |
| **BG4. Quản lý thanh toán tập trung**        | Quản lý cước và kết quả thanh toán, đồng thời tích hợp với nhà cung cấp thanh toán bên ngoài.     |
| **BG5. Tăng khả năng đáp ứng chuyến xe**     | Tự động tìm tài xế khác khi tài xế được đề xuất không phản hồi hoặc từ chối.                      |
| **BG6. Đảm bảo hệ thống ổn định và an toàn** | Đảm bảo hệ thống hoạt động khi tải cao, bảo vệ dữ liệu và kiểm soát quyền truy cập.               |
| **BG7. Hỗ trợ mở rộng trong tương lai**      | Dễ dàng bổ sung loại dịch vụ, phương thức thanh toán, kênh thông báo và các chức năng mới.        |
| **BG8. Hỗ trợ quản lý và ra quyết định**     | Cung cấp báo cáo về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả tài xế.         |

## Bước 4: Xác định phạm vi scope
**1. In Scope – Những gì hệ thống sẽ thực hiện**
| Nhóm                     | Phạm vi                                                                                  |
| ------------------------ | ---------------------------------------------------------------------------------------- |
| **Quản lý tài khoản**    | Đăng ký, đăng nhập, cập nhật thông tin khách hàng và tài xế.                             |
| **Đặt xe**               | Nhập điểm đón, điểm đến, chọn loại xe và gửi yêu cầu đặt xe.                             |
| **Tìm tài xế**           | Tự động tìm tài xế dựa trên vị trí, trạng thái và tiêu chí vận hành.                     |
| **Phân công tài xế**     | Gửi yêu cầu cho tài xế, xử lý nhận/từ chối/không phản hồi và tìm tài xế tiếp theo.       |
| **Theo dõi chuyến**      | Theo dõi vị trí tài xế và trạng thái chuyến đi.                                          |
| **Thực hiện chuyến**     | Tài xế cập nhật: đến điểm đón → đón khách → đang di chuyển → hoàn thành.                 |
| **Tính cước**            | Tính số tiền khách hàng phải trả dựa trên thông tin chuyến và loại dịch vụ.              |
| **Thanh toán**           | Hỗ trợ tiền mặt và thanh toán điện tử thông qua nhà cung cấp bên ngoài.                  |
| **Thông báo**            | Thông báo cho khách hàng/tài xế về đặt xe, nhận chuyến, trạng thái chuyến và thanh toán. |
| **Đánh giá**             | Khách hàng đánh giá tài xế sau khi hoàn thành chuyến.                                    |
| **Quản lý vận hành**     | Nhân viên quản lý khách hàng, tài xế, phương tiện và chuyến đi.                          |
| **Báo cáo**              | Báo cáo số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả tài xế.            |
| **Phân quyền & bảo mật** | Xác thực, phân quyền và ghi log các thao tác quan trọng.                                 |

**2. Out of Scope – Chưa nằm trong phạm vi**

Do dự án chỉ có 7 tuần, nên một số nội dung có thể xác định là ngoài phạm vi giai đoạn đầu:
Tự xây dựng cổng thanh toán riêng → chỉ tích hợp nhà cung cấp bên ngoài.
Tự xây dựng hạ tầng bản đồ/GPS → sử dụng dịch vụ bản đồ bên ngoài.
Xây dựng hệ thống quản lý lương và chấm công tài xế.
Quản lý bảo dưỡng, sửa chữa phương tiện.
Quản lý kho phụ tùng hoặc nhiên liệu.
Các dịch vụ khác ngoài đặt xe nếu chưa được ABC yêu cầu.
Các tính năng nâng cao chưa được xác định trong giai đoạn phân tích.

## Bước 5: Chuyển đổi business requirement
Từ Business Goal + Scope, ta chuyển nhu cầu kinh doanh thành các Business Requirement (BR) cụ thể.
| **Business Goal**                         | **Business Requirement**                                                                                     | **Mục đích/giá trị**                                        |
| ----------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------- |
| **BG1 – Tự động hóa đặt xe**              | **BR01:** Hệ thống cho phép khách hàng tạo yêu cầu đặt xe.                                                   | Giúp khách hàng đặt xe nhanh chóng, giảm thao tác thủ công. |
| **BG1 – Tự động hóa đặt xe**              | **BR02:** Hệ thống tự động tìm và phân công tài xế phù hợp.                                                  | Giảm thời gian tìm tài xế và nâng cao hiệu quả vận hành.    |
| **BG1 – Tự động hóa đặt xe**              | **BR03:** Hệ thống tiếp tục tìm tài xế khác khi tài xế từ chối hoặc không phản hồi.                          | Tăng khả năng tìm được tài xế cho khách hàng.               |
| **BG2 – Nâng cao trải nghiệm khách hàng** | **BR04:** Hệ thống cho phép khách hàng theo dõi trạng thái và vị trí chuyến đi.                              | Khách hàng chủ động nắm được tình trạng chuyến xe.          |
| **BG2 – Nâng cao trải nghiệm khách hàng** | **BR05:** Hệ thống cho phép khách hàng xem lịch sử và đánh giá tài xế.                                       | Nâng cao trải nghiệm và chất lượng dịch vụ.                 |
| **BG3 – Nâng cao hiệu quả vận hành**      | **BR06:** Hệ thống cho phép nhân viên quản lý khách hàng, tài xế, phương tiện và chuyến đi.                  | Quản lý tập trung, giảm công việc thủ công.                 |
| **BG4 – Quản lý thanh toán**              | **BR07:** Hệ thống tính cước và hỗ trợ thanh toán tiền mặt hoặc điện tử.                                     | Quản lý doanh thu và thanh toán thuận tiện.                 |
| **BG5 – Tăng khả năng đáp ứng chuyến**    | **BR08:** Hệ thống lưu vị trí và trạng thái hoạt động của tài xế.                                            | Hỗ trợ tìm tài xế gần khách hàng và rút ngắn thời gian chờ. |
| **BG6 – Ổn định và bảo mật**              | **BR09:** Hệ thống xác thực, phân quyền và bảo vệ dữ liệu người dùng.                                        | Đảm bảo an toàn và bảo mật thông tin.                       |
| **BG7 – Khả năng mở rộng**                | **BR10:** Hệ thống cho phép tích hợp thêm dịch vụ, phương thức thanh toán và kênh thông báo.                 | Giúp hệ thống dễ phát triển trong tương lai.                |
| **BG8 – Hỗ trợ ra quyết định**            | **BR11:** Hệ thống cung cấp báo cáo về số chuyến, doanh thu, tỷ lệ hoàn thành, tỷ lệ hủy và hiệu quả tài xế. | Giúp ban lãnh đạo theo dõi và ra quyết định.                |

## Bước 6: 




