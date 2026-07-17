# 🧠 AI Skill Kit — Quy chuẩn làm việc với AI

Bộ tài liệu cá nhân dùng để "onboard" AI trước khi bắt đầu bất kỳ dự án
nào. Thay vì giải thích lại từ đầu mỗi lần, chỉ cần cho AI đọc 3 file này
là sẵn sàng làm việc đúng chuẩn.

---

## 📁 Cấu trúc repo

```
ai-skill-kit/
├── README.md                        # File này
├── ai-onboarding-start.md           # Bước 1 — paste vào đầu mỗi dự án
├── system-prompt-engineer.md        # Luật làm việc (6 luật)
└── huong-dan-debug-overlay.md       # Kỹ thuật debug overlay web/PWA
```

---

## 🚀 Cách dùng

### Mỗi khi bắt đầu dự án mới với AI:

**Bước 1** — Paste nội dung `ai-onboarding-start.md` vào đầu conversation

**Bước 2** — Paste tiếp nội dung `system-prompt-engineer.md`

**Bước 3** — Paste tiếp nội dung `huong-dan-debug-overlay.md`

**Bước 4** — Đợi AI xác nhận theo mẫu `[ONBOARDING COMPLETE]`

**Bước 5** — Bắt đầu mô tả dự án

> Nếu AI xác nhận thiếu hoặc tóm tắt sai → sửa ngay tại bước này trước
> khi giao việc.

---

## 📄 Mô tả từng file

### `ai-onboarding-start.md`
File khởi động — paste vào **đầu tiên** mỗi cuộc trò chuyện. Yêu cầu AI
đọc 2 tài liệu còn lại và xác nhận đã hiểu theo cấu trúc chuẩn trước khi
nhận việc.

### `system-prompt-engineer.md`
Bộ luật làm việc gồm 6 luật:

| Luật | Nội dung |
|---|---|
| Luật 0 | Quy tắc nền — không có `[GO]` thì không được làm gì |
| Luật 1 | Nhận tính năng mới — grilling trước, code sau |
| Luật 2 | Fix bug — tái hiện lỗi trước, sửa sau |
| Luật 3 | Deploy / tech stack — ưu tiên bộ tool nhanh, dễ, miễn phí |
| Luật 4 | Thiết kế UX/UI — HTML tĩnh + Tailwind, mobile-first, hỏi trước khi design |
| Luật 5 | Báo cáo sau khi thực thi — done report bắt buộc |
| Luật 6 | Quản lý context dài — dùng `[STATUS?]` để track trạng thái |

Bảng lệnh điều phối nhanh:

| Lệnh | Ý nghĩa |
|---|---|
| `[GO]` | Xác nhận kế hoạch, bắt đầu thực thi |
| `[QUICK]` | Bypass quy trình, làm ngay (task < 20 dòng) |
| `[STOP]` | Dừng ngay lập tức |
| `[REPLAN]` | Lên kế hoạch lại |
| `[STATUS?]` | Báo cáo đang ở bước nào |

### `huong-dan-debug-overlay.md`
Tài liệu kỹ thuật về debug overlay cho web/PWA — hiện thông số debug
(kích thước, biến số, trạng thái) ngay trên màn hình bằng chữ xanh lá nền
đen, không cần remote debug qua máy tính. Gồm:

- 4 cách bật overlay (luôn bật / URL / localStorage / display-mode)
- Bảng giá trị sẵn có của trình duyệt (viewport, dpr, orientation...)
- `visualViewport` API cho PWA standalone
- Trigger resume khi app từ background trở về
- Hướng dẫn xóa sạch trước khi deploy

---

## 🛠️ Tech stack mặc định trong bộ luật

### Deploy & Hosting
- **Cloudflare Pages** — web tĩnh, CDN toàn cầu, miễn phí
- **GitHub Pages** — thay thế đơn giản hơn

### Backend & Lưu trữ
- **Cloudflare Workers** — serverless logic nhẹ, không trạng thái
- **Render.com** — backend thật (Node/Python/Docker), cron job, websocket — dùng khi Workers không đủ
- **Workers KV** — key-value storage
- **Cloudflare D1** — database SQL (SQLite at edge)
- **Cloudflare R2** — lưu file/ảnh (S3-compatible)

### Build & Automation
- **Google Colab** — compile nặng (C/C++ → WebAssembly, Python build)
- **GitHub Actions** — CI/CD tự động

### Tích hợp
- **Google Apps Script** — Google Sheets, Docs, Gmail, Drive

### UI
- **HTML tĩnh + Tailwind CSS** — mobile-first, responsive cho cả
  mobile / desktop / PWA

---

## 📝 Ghi chú

Repo này là tài liệu sống — cập nhật liên tục khi có quy tắc hoặc kỹ
thuật mới tích lũy được qua thực tế làm dự án.
