# Bài 5: Khởi chạy dịch vụ đơn giản với Docker Compose

## 1. Cấu hình `docker-compose.yml`

```yaml
services:
  web:
    image: nginx:alpine
    ports:
      - "8082:80"
```

---

## 2. Các bước thực hiện & Kiểm tra

### Bước 1: Khởi chạy dịch vụ
```bash
docker compose up -d
```
**Kết quả:**
```text
[+] up 13/13
 ✔ Image nginx:alpine   Pulled
 ✔ Network bai5_default Created
 ✔ Container bai5-web-1 Started
```

### Bước 2: Kiểm tra trạng thái dịch vụ
```bash
docker compose ps
```
**Kết quả:**
```text
NAME         IMAGE          COMMAND                  SERVICE   CREATED          STATUS          PORTS
bai5-web-1   nginx:alpine   "/docker-entrypoint.…"   web       12 seconds ago   Up 12 seconds   0.0.0.0:8082->80/tcp, [::]:8082->80/tcp
```

### Bước 3: Kiểm tra truy cập web (Nginx)
```bash
curl http://localhost:8082
```
**Kết quả:** Trả về mã trạng thái HTTP 200 và trang HTML chào mừng mặc định của Nginx (`Welcome to nginx!`).

```text
StatusCode        : 200
StatusDescription : OK
Content           : <!DOCTYPE html>
                    <html>
                    <head>
                    <title>Welcome to nginx!</title>
...
```

### Bước 4: Hạ và dọn dẹp dịch vụ
```bash
docker compose down
```
**Kết quả:**
```text
[+] down 2/2
 ✔ Container bai5-web-1 Removed
 ✔ Network bai5_default Removed
```
