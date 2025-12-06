# 📱 Hướng Dẫn Chạy Hệ Thống Đặt Món CAFE M.I.N

## ✅ Giải Pháp Đơn Giản (Không Cần Server)

Tôi đã cập nhật hệ thống để dùng **localStorage** - lưu đơn hàng trên trình duyệt. Cách này hoạt động **100% offline** trên máy tính của bạn!

### 🚀 Cách Chạy (Dễ Nhất)

**Cách 1: Chạy file HTML trực tiếp**
- Mở **index.html** trên trình duyệt (trang khách đặt món)
- Mở **admin.html** trên trình duyệt khác/tab khác (trang quầy nhận đơn)
- Đặt món trên index.html → **admin.html sẽ tự động cập nhật** ✨

**Cách 2: Dùng Live Server (VS Code)**
- Cài extension "Live Server" cho VS Code
- Click chuột phải file HTML → "Open with Live Server"
- Mở http://localhost:5500/index.html
- Mở http://localhost:5500/admin.html ở tab khác

**Cách 3: Chạy HTTP Server**
```powershell
# Mở PowerShell trong thư mục project
cd "c:\Users\tran vu\Desktop\New folder (3)"

# Chạy Python server (nếu có Python)
python -m http.server 8000

# Hoặc dùng Node.js nếu cài
npx http-server
```
Sau đó mở: http://localhost:8000/index.html

---

## 🎯 Cách Sử Dụng

### 👤 Trang Khách (index.html)
1. Chọn "TẠI QUÁN" hoặc "GIAO HÀNG"
2. Nhập thông tin (số bàn hoặc địa chỉ)
3. Chọn món ăn và số lượng
4. Bấm "GỌI MÓN" → Xác nhận → "GỬI ĐƠN CHO QUẦY"
5. ✅ Đơn được lưu ngay!

### 🍽️ Trang Quầy (admin.html)
- Hiện **danh sách tất cả đơn hàng**
- Có thống kê: Chờ làm / Đã xong / Tổng tiền
- Bấm "ĐÃ XONG" để đánh dấu hoàn thành
- Bấm "Xóa" để xóa từng đơn
- Bấm "XÓA HẾT" để xóa tất cả
- **Tự động phát âm thanh khi có đơn mới** 🔔

---

## 💾 Dữ Liệu Lưu Ở Đâu?

Tất cả đơn hàng được lưu trong **localStorage** của trình duyệt:
- Mỗi trình duyệt / profile khác nhau = dữ liệu khác nhau
- Nếu xóa cache → mất dữ liệu (nên backup định kỳ)

**Để sao lưu dữ liệu:**
1. Mở admin.html
2. Mở DevTools (F12)
3. Console: `copy(JSON.stringify(JSON.parse(localStorage.getItem('orders')), null, 2))`
4. Dán vào file `.txt` để lưu trữ

---

## 🌐 Nếu Muốn Deploy Lên Internet

### Option A: Vercel (Dễ nhất)
```powershell
# Cài Vercel CLI
npm install -g vercel

# Chạy từ thư mục project
cd "c:\Users\tran vu\Desktop\New folder (3)"
vercel
```
Sau đó Vercel sẽ cho bạn URL công khai!

### Option B: Netlify
Drag & drop thư mục vào https://app.netlify.com

### Option C: GitHub Pages
Push lên GitHub, bật GitHub Pages trong Settings

---

## 📝 Thay Đổi / Tùy Chỉnh

**Thêm/Sửa menu:** Chỉnh sửa file `index.html` phần `<div class="menu">...</div>`

**Thay đổi màu sắc:** Tìm `:root` ở phía trên style.css, sửa các biến:
```css
--gold: #f9b700;      /* Vàng */
--red: #ff4444;       /* Đỏ */
--green: #25d366;     /* Xanh */
```

**Thay đổi tên quán:** Tìm "CAFE M.I.N" thay thế bằng tên của bạn

---

## ❓ Lỗi Thường Gặp

**Q: Trang quầy không nhận đơn?**
- A: Đảm bảo 2 tab dùng cùng trình duyệt (Chrome, Firefox, Edge)
- Refresh trang admin

**Q: Âm thanh không phát?**
- A: Bật Volume trình duyệt
- Hoặc thay đổi URL âm thanh trong admin.html

**Q: Dữ liệu mất khi đóng trình duyệt?**
- A: Bình thường - localStorage chỉ lưu trong session
- Để lưu vĩnh viễn cần database (Firebase, MongoDB)

---

## 🔥 Upgrade Tiếp Theo (Nếu Cần)

1. **Database thật** (Firebase/Supabase) - lưu vĩnh viễn
2. **Push Notification** - thông báo trên điện thoại
3. **QR Code** - khách quét QR tại bàn để đặt món
4. **In hóa đơn** - tích hợp máy in
5. **Mobile App** - ứng dụng mobile native

---

## 📞 Support
Nếu cần giúp, hãy kiểm tra DevTools (F12) → Console để xem có lỗi gì không!

Chúc bạn thành công! 🎉
