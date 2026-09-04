# YOVIES CINEMAS — NETLIFY FREE

Bản này đã được chuyển từ Express + SQLite sang kiến trúc Netlify Functions + Netlify Database (Postgres) + Netlify Blobs.

## Deploy nhanh

1. Upload project này lên GitHub.
2. Netlify → Add new project → Import an existing project → GitHub → chọn repository.
3. Giữ Build command: `npm run build` và Publish directory: `public`.
4. Netlify → Data & Storage → Database → Create database. Netlify Database sẽ cung cấp kết nối cho Functions.
5. Netlify → Project configuration → Environment variables → thêm các biến trong `.env.example`.
6. Với Gmail OTP, dùng Gmail + App Password. Không đưa mật khẩu vào code/GitHub.
7. Với Google Login, tạo OAuth Client ID và thêm domain `https://TEN-SITE.netlify.app` vào Google OAuth allowed origins.
8. Deploy lại.
9. Trang chính: `/`
10. Admin: `/admin/`

## Admin

Nên đặt `ADMIN_EMAIL` và `ADMIN_PASSWORD` riêng trước deploy. Không dùng mật khẩu mẫu trên môi trường public.

## Database

Migration nằm tại `netlify/database/migrations/0001_initial.sql`.

## Upload

Proof task và media poster/video được lưu vào Netlify Blobs. Netlify Functions giới hạn request buffered, vì vậy video upload qua Admin chỉ phù hợp file nhỏ; với phim lớn hãy dùng URL streaming/video storage riêng và nhập URL vào trường Video URL.

## Tính năng

- Đăng ký Gmail + OTP
- Đăng nhập mật khẩu
- Google Login
- Quên mật khẩu + OTP
- Session cookie ký server-side
- Yoin server-side
- Invite +15/+10, single-use
- Mua vé + transaction atomic
- Vé one-time viewing
- Task proof + admin approve/reject +30/-5
- Admin dashboard/users/tickets/tasks/movies
- Netlify Database persistence
- Netlify Blobs upload persistence

## Lưu ý Free

Netlify Free là gói $0 với giới hạn credits. Database/Functions/Blobs đều có hạn mức. Không dùng Netlify Free để stream thư viện phim dung lượng lớn.
