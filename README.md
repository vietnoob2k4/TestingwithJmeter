# TestingwithJmeter
# BÁO CÁO KIỂM THỬ HIỆU SUẤT

## 1. Thiết lập kịch bản kiểm thử

### Mô phỏng
- **Số lượng người dùng:** 50 người dùng đồng thời truy cập trang web trong 5 phút.
- **Loại kiểm thử:** Kiểm thử tải (Load Testing) và kiểm thử khả năng chịu tải (Stress Testing).
- **Mô phỏng hành vi:** Gửi yêu cầu HTTP đến trang chủ của website.

### Mục tiêu
- Đo thời gian phản hồi trung bình.
- Xác định bottleneck nếu có.
- Theo dõi throughput và tỷ lệ lỗi.

## 2. Kết quả kiểm thử

### 2.1. Kiểm thử tải (Load Testing)
- **Số lượng người dùng:** Tăng từ 10 đến 50.
- **Thống kê thời gian phản hồi:**
  - Trung bình: 104 ms
  - Median: 93 ms
  - 90% Line: 109 ms
  - 95% Line: 118 ms
  - 99% Line: 567 ms
  - Min: 81 ms
  - Max: 567 ms
- **Tỷ lệ lỗi:** 0%
- **Throughput:** 1.7 requests/giây
- **Lưu lượng dữ liệu:**
  - Nhận: 3.65 KB/giây
  - Gửi: 0.21 KB/giây

**Kết luận:** Hệ thống hoạt động ổn định với 50 người dùng đồng thời, không phát hiện lỗi.

### 2.2. Kiểm thử khả năng chịu tải (Stress Testing)
- **Số lượng người dùng:** Tăng lên 199508 yêu cầu.
- **Thống kê thời gian phản hồi:**
  - Trung bình: 143 ms
  - Median: 150 ms
  - 90% Line: 191 ms
  - 95% Line: 204 ms
  - 99% Line: 262 ms
  - Min: 26 ms
  - Max: 21694 ms
- **Tỷ lệ lỗi:** 72.04%
- **Throughput:** 351.4 requests/giây
- **Lưu lượng dữ liệu:**
  - Nhận: 1486.21 KB/giây
  - Gửi: 43.56 KB/giây

**Kết luận:** Khi tải tăng cao, hệ thống bắt đầu quá tải, thời gian phản hồi tăng và tỷ lệ lỗi cao.

## 3. Phân tích và đề xuất cải tiến

### 3.1. Tại sao kiểm thử phi chức năng quan trọng?
- Kiểm thử hiệu suất giúp xác định giới hạn chịu tải của hệ thống.
- Đảm bảo trải nghiệm người dùng không bị gián đoạn.
- Giúp phát hiện bottleneck trước khi triển khai sản phẩm thực tế.

### 3.2. Các thông số quan trọng cần theo dõi
- Thời gian phản hồi trung bình, 90%, 95%, 99% Line.
- Throughput (số lượng yêu cầu/giây).
- Tỷ lệ lỗi (%).
- Dung lượng dữ liệu nhận/gửi.

### 3.3. Đề xuất cải thiện hiệu suất
- **Tối ưu hóa truy vấn cơ sở dữ liệu:** Giảm thời gian phản hồi.
- **Tăng cường caching:** Sử dụng Redis/Memcached để giảm tải.
- **Cân bằng tải (Load Balancing):** Phân phối yêu cầu giữa nhiều server.
- **Mở rộng hệ thống (Scaling):** Sử dụng auto-scaling để mở rộng linh hoạt.
- **Tối ưu hóa code backend:** Kiểm tra bottleneck trong API.

## 4. Kết luận
- Hệ thống hoạt động ổn định với 50 người dùng.
- Khi tải tăng cao (hơn 199K yêu cầu), hệ thống giảm hiệu suất và tỷ lệ lỗi tăng mạnh.
- Cần tối ưu backend, sử dụng caching và cân bằng tải để cải thiện hiệu suất.
## 5.Minh họa
- Kết quả khi có 50 người dùng truy cập hệ thống:
  ![Ảnh chụp màn hình 2025-02-08 202908](https://github.com/user-attachments/assets/058024ad-b76a-4aca-b69f-90d2e92087f8)
- Kết quả khi có 100 người dùng truy cập hệ thống:
  ![Ảnh chụp màn hình 2025-02-08 203757](https://github.com/user-attachments/assets/74b82391-0680-4915-99ee-1a4a7e6c8873)


