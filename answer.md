1.Khi bạn gõ https://shopee.vn vào trình duyệt và nhấn Enter, hãy liệt kê đúng thứ tự ít nhất 5 bước xảy ra (từ DNS lookup đến render).
Trả lời :
1. DNS Lookup : trình duyệt sẽ hỏi dns server : shopê.vn là gì => nhận địa chỉ ip của server
2. Thiết lập kết nối (TCP + TLS) : tạo kết nối với tcp là server , nếu là https -> thêm bước tls handshake để mã hóa bảo mật
3. Gửi HTTP Request : gửi rq đến server shopee
4. Server xử lý : Server nhận rq -> xử lý logic (lấy dữ liệu , render html , gọi db,..)
5. Server trả http response : trả về html , css ,js , ...
6. Browser tải thêm tài nguyên : trình duyệt tiếp tục gửi nhiều rq khác để tải : css , js , ảnh ( khoảng 50-100 rq)
7. Browser Rendering : 
- Parse HTML -> Tạo DOM
- Parse CSS
- Execute JS
- Paint & Render -> hiển thị trang web
2.Trong DevTools của Chrome, tab Network cho thấy thông tin gì? Hãy mở một trang web bất kỳ, chụp screenshot tab Network và đánh dấu (vẽ mũi tên/khoanh tròn) vào:
-Status Code của request đầu tiên
-Tổng thời gian load trang
-Một request trả về file CSS
Trả lời : 
![alt text](image.png)
Status Code của request đầu tiên : Status = 200
Tổng thời gian load trang : Finish: 10.58 s
Một request trả về file CSS : 8434.0c54badf654b474e.2023.css
-> Đây là request trả về file CSS
Câu A2 (5đ) — Semantic HTML
Đọc chương 04, trả lời: Tại sao trang web dưới đây bị Google đánh giá SEO thấp? Liệt kê ít nhất 4 lỗi semantic và sửa lại.

<div class="header">
    <div class="logo">ShopTLU</div>
    <div class="menu">
        <div><a href="/">Trang chủ</a></div>
        <div><a href="/products">Sản phẩm</a></div>
    </div>
</div>
<div class="main">
    <div class="product">
        <div class="title">iPhone 16 Pro</div>
        <div class="price">25.990.000đ</div>
        <div class="image"><img src="iphone.jpg"></div>
    </div>
</div>
<div class="footer">© 2026 ShopTLU</div>
Trả lời :
Tại sao trang web bị SEO thấp vì :

- Trang web sử dụng quá nhiều thẻ <div> không có ý nghĩa khiến:
+,Google không hiểu cấu trúc trang
+,Không biết đâu là header, nội dung chính, sản phẩm...
+,SEO kém (đúng như chương 4 nói: dùng sai thẻ = Google không hiểu nội dung)
- Các lỗi semantic :
Lỗi 1: Dùng <div class="header"> thay vì <header>
Không thể hiện đây là phần đầu trang
Lỗi 2: Menu không dùng <nav>
<div class="menu">
Lỗi 3: Nội dung chính không dùng <main>
<div class="main">
Lỗi 4: Sản phẩm không dùng <article>
<div class="product">
Lỗi 5: Không dùng <section> để nhóm nội dung
Không chia rõ khu vực nội dung

Câu A3 (5đ) — Block vs Inline
Không chạy code, hãy vẽ tay (hoặc mô tả bằng text art) kết quả hiển thị của đoạn HTML sau. Giải thích tại sao.

<div>Hộp 1</div>
<span>Text A</span>
<span>Text B</span>
<div>Hộp 2</div>
<span>Text C</span>
<strong>Text D</strong>
<div>Hộp 3</div>
Trả lời :

-<div> là **block element** → chiếm toàn bộ 1 dòng → luôn xuống dòng.
-<span> và <strong> là **inline element** → chỉ chiếm nội dung → nằm cùng dòng.

- <div>Hộp 1</div> → hiển thị riêng 1 dòng  
- <span>Text A</span> <span>Text B</span> → cùng dòng → "Text A Text B"  
- <div>Hộp 2</div> → xuống dòng  
- <span>Text C</span> <strong>Text D</strong> → cùng dòng → "Text C Text D"  
- <div>Hộp 3</div> → xuống dòng  

=>

- Block element → xuống dòng  
- Inline element → nằm cùng dòng

Câu A4 (5đ) — Table
Đọc chương 05. Giải thích sự khác nhau giữa <thead>, <tbody>, <tfoot>. Tại sao KHÔNG NÊN dùng table để tạo layout trang web? (Ghi rõ ít nhất 3 lý do)
Trả lời : 
- <thead> là phần đầu của bảng , chứa tiêu đề các cột 
- <tbody> là phần thân bảng , chứa dữ liệu chính
- <tfoot> là phần cuối bảng , hiển thị thông tin tổng kết
2. Tại sao k nên dùng <table> để layout trang web
LD1 : Sai semantic ( ý nghĩa html )
- <table> chỉ nên dùng cho dữ liệu bảng
- Dùng layout sẽ làm sai ý nghĩa -> ảnh hưởng SEO , google khó hiểu cấu trúc trang
LD2 : Khó responsive
- Table có cấu trúc cứng, khó co giãn trên nhiều kích thước màn hình.
- Khi hiển thị trên mobile dễ bị vỡ layout.
ld3 : Code phức tạp, khó bảo trì
- Phải dùng nhiều thẻ <tr>, <td> lồng nhau.
- Code dài, khó đọc, khó sửa.
LD4 : Hiệu năng kém hơn
- Trình duyệt phải load toàn bộ bảng rồi mới render.
- Kém tối ưu hơn so với layout bằng CSS (Flexbox, Grid).