# Suricata + ELK Stack Lab
**Tác giả:** Nguyễn Bảo Quang — ĐH Thủy Lợi

## Mục tiêu
Triển khai mô hình giám sát mạng: **Suricata (IDS)** → **Filebeat** → **Elasticsearch** → **Kibana** để minh họa pipeline SIEM và viết rule tùy chỉnh.

## Nội dung chính
- File cấu hình Suricata: `suricata.yaml` (rule path)
- Custom rules: `custom.rules`
- Cấu hình Filebeat: `filebeat.yml` (đọc `/var/log/suricata/eve.json`)
- Ảnh minh họa dashboard nằm trong `screenshots/`

## Cách test nhanh
1. Kích hoạt rule (restart Suricata): `sudo systemctl restart suricata`
2. Sinh traffic:
   - `ping 8.8.8.8` → sinh ICMP alert
   - `curl http://example.com` → HTTP alert
   - `ssh localhost` → SSH alert
   - `nslookup google.com` → DNS alert
3. Mở Kibana → Discover → filter: `event.module: suricata AND event.kind: alert`

## Thư mục
suricata-elk/
├── custom.rules
├── filebeat.yml
├── suricata.yaml
└── screenshots/
