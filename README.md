# Bài 4 — `.gitignore` và sửa commit gần nhất

**Sinh viên:** NguyễnDăngDương
**Lớp:** CNTT2
**Môn học:** IT209 — Session 04

File `.gitignore` bỏ qua `credentials.txt`, file môi trường và private key để tránh đưa dữ liệu nhạy cảm vào các commit sau.

## Gỡ credentials khỏi commit hiện tại, giữ file trên máy

```bash
git rm --cached credentials.txt
git add .gitignore
git status
git commit --amend -m "Ignore local credentials"
git log -n 1 --oneline
git status
```

`git rm --cached` chỉ gỡ file khỏi Git index, không xóa file vật lý. Sau khi `.gitignore` được thêm, `credentials.txt` không bị Git theo dõi lại. `--amend` thay commit gần nhất và cập nhật message.

Nếu credentials đã được push hoặc xuất hiện trong commit cũ hơn, cần thu hồi/thay secret ngay; amend commit mới nhất không xóa dữ liệu khỏi toàn bộ lịch sử đã chia sẻ.
