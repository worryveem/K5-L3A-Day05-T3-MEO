# Prototype — T3 · Trợ lý đổi chuyến khi chuyến bay bị huỷ

Người dựng: Đỗ Minh Hoàng (C) · 2A202603554

## Chạy

- File: [`index.html`](index.html). Chỉ dùng HTML, CSS và JS thuần, không cài thư viện, không có backend.
- Mở `index.html` trực tiếp bằng trình duyệt, hoặc chạy `python -m http.server 5500` ở thư mục gốc repo rồi mở http://localhost:5500/prototype/

## Nội dung

| Màn | Kịch bản | Có gì |
|---|---|---|
| B1 | KB-A "ok đổi sang chuyến tối nay luôn" | Thẻ BM 217 "Còn 1 / cần 2" không có nút nào · BM 201 và BM 205 tự giữ chỗ, mỗi chuyến một đồng hồ 20' · Nhả chỗ · Màn xác nhận đổi cả 2 người · Chọn lại phương án · Ca đổi nhầm → chuyển nhân viên |
| B2 | KB-B "thôi huỷ hết đi, hoàn tiền cho mình" | Khối hậu quả · Chuyến thay thế đang giữ · Bản nháp do AI soạn, khách tự gửi · Ô tick từng hành khách · Hoàn riêng một người → chuyển nhân viên |

**Thanh DEMO** (màu đen, không thuộc sản phẩm):
- Chuyển giữa B1 và B2.
- **⏩ Tua 5 phút**: xem nhắc hạn và hết hạn mà không phải chờ.
- **↺ Chạy lại**.
- **Hiện số đánh dấu**: bật số ①–⑧ dùng cho ảnh.
- **Mô phỏng tool lỗi**: giữ chỗ BM 205, nhả chỗ, đổi vé và chuyển nhân viên đều thất bại.

## Phần mock

- Toàn bộ dữ liệu lấy từ §2 spec.md: TRV-7Q2K, BM 213, BM 217/201/205, tra cứu lúc 15:00 12/11/2026.
- Mọi lệnh tool (`tra_cuu_dat_cho`, `giu_cho_chuyen_moi`, `nha_cho_dang_giu`, `doi_chuyen_bay`, `soan_yeu_cau_hoan_ve`, gửi hoàn, `chuyen_nhan_vien`) chỉ là hàm JS có độ trễ giả. Không kết nối hệ thống đặt vé nào.
- Câu AI nói lấy nguyên văn §3. Những câu §3 chưa có nằm trong `COPY_C`, do C soạn và B duyệt.
- **Nhật ký hành động** (cuối cột trái) ghi từng lệnh tool đã chạy, kèm "ai kích hoạt", và cả những lần AI **không gọi** tool. Dùng nhật ký này để tách lời AI nói với hành động thật khi chấm T1–T3.
- **Không có lời gọi AI thật.** Hội thoại đi theo kịch bản bằng chip gợi ý.

## Ảnh

| Ảnh | Trạng thái |
|---|---|
| [anh-1-b1-giu-cho.png](anh/anh-1-b1-giu-cho.png) | B1 sau khi tra cứu và giữ chỗ, trước khi khách chọn (①–④) |
| [anh-2-b1-xac-nhan.png](anh/anh-2-b1-xac-nhan.png) | Màn xác nhận đổi cả 2 người sang BM 201 |
| [anh-3-b2-hoan-ve.png](anh/anh-3-b2-hoan-ve.png) | B2: bản nháp hoàn, ba cảnh báo ngay trên nút gửi (⑤–⑧) |
