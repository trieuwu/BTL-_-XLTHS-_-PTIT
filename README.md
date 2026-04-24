# HỆ THỐNG PHÂN TÁCH TÍN HIỆU DTMF (DUAL-TONE MULTI-FREQUENCY)

Dự án này là một phần của học phần **Xử lý Tín hiệu Số (Digital Signal Processing)** thuộc chương trình đào tạo Lớp Tài năng - Học viện Công nghệ Bưu chính Viễn thông (PTIT). Hệ thống thực hiện mô phỏng toàn bộ quy trình từ mã hóa phím bấm điện thoại, truyền dẫn qua kênh nhiễu, đến giải mã bằng hệ thống bộ lọc băng thông (Filter Bank).

---

## Giới thiệu dự án

Hệ thống DTMF là công nghệ tiêu chuẩn trong viễn thông dùng để mã hóa phím bấm thành các cặp tần số âm thanh (song âm). Dự án tập trung giải quyết ba bài toán chính:

- **Mã hóa (Encoder):** Tạo tín hiệu song âm chuẩn từ bàn phím số.
- **Mô phỏng kênh truyền:** Đánh giá độ bền tín hiệu dưới tác động của nhiễu trắng cộng (AWGN).
- **Giải mã (Decoder):** Sử dụng hệ thống 7 bộ lọc FIR (thiết kế theo phương pháp cửa sổ) để tách trích tần số và nhận diện ký tự ban đầu.

---

## Hướng dẫn đọc báo cáo

Báo cáo được trình bày theo trình tự logic kỹ thuật, nên đọc theo thứ tự sau:

- **Chương 1 & 2:**  
  Cơ sở lý thuyết về chuẩn DTMF, biến đổi Fourier nhanh (FFT) và nguyên lý thiết kế bộ lọc FIR.

- **Chương 3 (Trọng tâm):**  
  Quy trình thiết kế hệ thống trên MATLAB, phương pháp xác định bậc bộ lọc \( N = 150 \) và lựa chọn cửa sổ Hamming.

- **Chương 4:**  
  Phân tích kết quả thực nghiệm, bao gồm:
  - Đáp ứng tần số (freqz)
  - Phân tích cực - không (zplane)

- **Chương 5:**  
  Đánh giá hiệu năng giải mã theo các mức SNR khác nhau và đề xuất hướng phát triển.

---

## Hướng dẫn sử dụng phần mềm MATLAB

### 1. Yêu cầu hệ thống

- MATLAB phiên bản R2019b trở lên  
- Đã cài đặt **Signal Processing Toolbox**

---

### 2. Cách khởi chạy

1. Mở phần mềm MATLAB  
2. Điều hướng đến thư mục chứa file `DTMF_App.mlapp`  
3. Mở ứng dụng bằng một trong hai cách:
   - Nhập lệnh `appdesigner` và mở file
   - Double-click trực tiếp vào file `DTMF_App.mlapp`
4. Nhấn **Run** để khởi chạy giao diện

---

### 3. Thao tác trên giao diện

- **Nhập liệu:**  
  Nhấn các phím `0-9`, `*`, `#` trên bàn phím GUI

- **Mô phỏng nhiễu:**  
  Điều chỉnh thanh trượt **SNR (dB)** để thay đổi mức nhiễu của kênh truyền

- **Phân tích tín hiệu:**
  - Quan sát đồ thị miền thời gian để kiểm tra dạng sóng song âm
  - Quan sát phổ FFT để xác định các đỉnh tần số hàng/cột

- **Giải mã:**
  - Kết quả hiển thị tại ô **"Decoded Result"**
  - Đèn trạng thái (Lamp):
    - Màu xanh: nhận diện thành công
    - Màu khác: tín hiệu không được nhận diện chính xác

---
