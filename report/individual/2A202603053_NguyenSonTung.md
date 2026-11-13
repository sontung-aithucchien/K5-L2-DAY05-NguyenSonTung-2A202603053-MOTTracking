# Báo cáo cá nhân — Nguyễn Sơn Tùng (2A202603053)

Đổi tên file theo quy tắc `MSSV_HoTen.md`. Ví dụ: `20241234_NguyenVanAn.md`.

Đoạn video: MOT17-09, 150 frame (frame 1–150), nguồn MOTChallenge, giấy phép CC BY-NC-SA 3.0.

## 0. Thông tin học viên

- Họ tên: Nguyễn Sơn Tùng
- MSSV: 2A202603053
- Mã đề (A/B/C): A
- Email: 26ai.tungns2@vinuni.edu.vn
- Link repository: https://github.com/sontung-aithucchien/K5-L2-DAY05-NguyenSonTung-2A202603053-MOTTracking
- Giờ bắt đầu: 16:30 13/11/2026
- Giờ kết thúc: 19:30 13/11/2026

## 1. Xem trước đoạn video (CP0)

Ghi **trước khi vẽ**, mỗi người một dòng. CP0 gốc chưa được lưu; các mốc dưới đây được hồi cứu từ exports.

| Mã | Frame xuất hiện | Frame cuối thấy được | Rẽ / dừng / đổi tốc độ ở frame | Bị che ở frame | Ghi chú |
|---|---|---|---|---|---|
| P1 | 0 | 149 | Di chuyển sang phải đến khoảng 100, sau đó chậm/đổi hướng; box lớn dần | 30–54; khuất hẳn 41–48 | Track ở khu vực cửa hàng |
| P2 | 60 | 149 | Di chuyển sang phải đến khoảng 120, sau đó chậm/đổi hướng | 60–72 | Xuất hiện muộn; box lớn dần |
| P3 | 0 | 149 | Tiến từ phải sang trái và lại gần camera; box lớn dần | Không thấy cờ che | |
| P4 | 39 | 149 | Tiến từ phải sang trái và lại gần camera; box lớn dần rõ | Không thấy cờ che | Keyframe dày ở nhiều đoạn |
| P5 | 0 | 146 | Di chuyển ít, chủ yếu quanh một vị trí | Che một phần: 106–110, 136–139, 142–146; khuất hẳn: 111–135, 147–149 | Đứa trẻ; track này là P5 theo đề A |

## 2. Keyframe và thời gian (CP1, CP4)

Số keyframe lấy từ kết quả `src/check_submission.py`.

| Mã | Số keyframe | Keyframe ở frame | Số frame có mặt | Keyframe / 100 frame | Thời gian (phút) | Chỗ khó |
|---|---|---|---|---|---|---|
| P1 | 60 | 0, 10, 11, 12, 16, 17, 18, 20, 24, 25, 30, 40, 49, 50, 55, 56, 57, 58, 59, 60, 62, 63, 64, 65, 66, 67, 70, 73, 74, 75, 76, 80, 82, 84, 87, 89, 90, 92, 93, 94, 95, 96, 97, 98, 100, 101, 102, 103, 109, 110, 113, 114, 115, 116, 120, 130, 140, 143, 148, 149 | 142 | 42.3 | 14 | Khó ở đoạn che 30–55 |
| P2 | 25 | 60, 61, 65, 68, 69, 70, 72, 73, 74, 75, 76, 77, 78, 79, 80, 90, 100, 110, 120, 124, 125, 130, 140, 148, 149 | 90 | 27.8 | 8 | Xuất hiện muộn, có đoạn che 60–72 |
| P3 | 24 | 0, 10, 20, 24, 29, 30, 40, 50, 57, 60, 70, 80, 90, 95, 100, 110, 112, 120, 130, 140, 143, 144, 146, 149 | 150 | 16.0 | 8 | Lại gần camera, box lớn dần |
| P4 | 62 | 39, 41, 42, 43, 44, 45, 64, 65, 66, 67, 72, 77, 81, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 96, 97, 99, 100, 101, 102, 103, 104, 105, 106, 107, 108, 109, 110, 111, 112, 113, 114, 119, 128, 129, 130, 131, 132, 133, 134, 135, 136, 137, 138, 140, 141, 143, 144, 145, 146, 147, 148, 149 | 111 | 55.9 | 17 | Box tăng mạnh kích thước khi lại gần; keyframe dày quanh đoạn này |
| P5 | 18 | 0, 10, 20, 30, 40, 50, 60, 70, 80, 100, 106, 107, 110, 136, 138, 139, 140, 142 | 122 | 14.8 | 8 | Đứa trẻ; có đoạn che/khuất hẳn |
| **Tổng** | **189** | | **615** | **30.7** | **55** | |

Thời gian CP1 được phân bổ ước tính theo độ dày keyframe và độ khó (tổng 55 phút), không phải log thời gian thực.

Keyframe / 100 frame của cả bài = tổng keyframe ÷ tổng số frame có mặt × 100 = 189 ÷ 615 × 100 = **30.7**.

Bạn đặt keyframe nhiều nhất ở người nào? Vì sao (người đó rẽ, dừng, lại gần camera hay bị che)?

P4 có nhiều keyframe nhất (62); mật độ 55.9 keyframe / 100 frame. Box tăng từ khoảng 130×470 px ở frame 40 lên 305×950 px ở frame 149 khi người đó tiến gần camera; đây là lý do phù hợp cho một số keyframe dày, nhưng các keyframe gần nhau vẫn cần được rà để bỏ những điểm dư.

## 3. Đoạn bị che (CP2)

Người bị che: `P1`

| Mốc | Frame |
|---|---:|
| Bắt đầu bị che một phần (bật `occluded`) | 30 |
| Mất hẳn (bật `outside`) | 41 |
| Hiện lại (tắt `outside`) | 49 |
| Thấy rõ trở lại (tắt `occluded`) | 55 |

- Thời gian khuất hẳn: 8 frame = 0.27 giây.
- Quyết định: giữ cùng ID.
- Lý do (trả lời 3 câu: khuất bao lâu so với 60 frame, ngoại hình có khớp, chỗ hiện lại có đúng hướng và tốc độ):

P1 khuất hẳn 8 frame, ít hơn ngưỡng 60 frame. Khi xuất hiện lại, ngoại hình và hướng di chuyển tiếp nối người trước đó, nên tôi giữ cùng ID P1.

Ảnh CP2 của P1 cần được chụp lại trên CVAT trước khi nộp, ghi đè các ảnh P5 hiện tại:

- `che_1_truoc.png`: frame 29, P1 còn thấy rõ.
- `che_2_giua.png`: frame 41–48, P1 không có box trên ảnh nhưng track còn trong panel và `outside` bật.
- `che_3_sau.png`: frame 55, cùng ID P1 và đã tắt `occluded`.

Ba ảnh hiện có minh họa P5 (đứa trẻ), nên không dùng làm minh chứng CP2 cho P1.

## 4. Tự review ID (CP3)

Lượt 1 theo người (đi ngược từ frame 149 về 0 trên CVAT), lượt 2 theo cảnh (nhảy 10 frame). Ít nhất 3 dòng; không có lỗi thì ghi một dòng "đã kiểm hai lượt, không lỗi".

Rà soát có hỗ trợ bằng AI và exports: lượt 1 theo từng P1–P5, lượt 2 theo cảnh mỗi 10 frame. 150/150 frame có cùng box giữa CVAT for image và CVAT for video; kiểm tra chuyển động liền kề không thấy bước nhảy box bất thường. Không phát hiện lỗi ID/box rõ ràng trong dữ liệu hiện có.

Loại lỗi dùng đúng một trong 7 mã: `id_switch`, `fragmentation`, `lost`, `merge`, `false_track`, `drift`, `flag`.

| Frame | Mã người | Loại lỗi | Mô tả một câu | Phát hiện ở lượt | Đã sửa? |
|---:|---|---|---|---|---|
| — | — | — | Đã kiểm hai lượt, không phát hiện lỗi rõ ràng trong exports. | Lượt 1 + lượt 2 | Không cần sửa |

Tổng hợp số lỗi theo loại:

| `id_switch` | `fragmentation` | `lost` | `merge` | `false_track` | `drift` | `flag` |
|---:|---:|---:|---:|---:|---:|---:|
| 0 | 0 | 0 | 0 | 0 | 0 | 0 |

Các số 0 là lỗi không phát hiện trong lần rà soát exports này; chưa phải kết quả đối chiếu với ground truth.

Lỗi nào chỉ lượt 2 (theo cảnh) mới thấy, lượt 1 (theo người) không thấy? Vì sao?

Không có lỗi chỉ lượt 2 mới phát hiện trong lần rà soát exports này.

## 5. File xuất và kết quả tự kiểm (CP4)

| Kiểm tra | Kết quả |
|---|---|
| Tên file MOT 1.1 | `NguyenSonTung_mot.zip` |
| Tên file CVAT for video 1.1 | `NguyenSonTung_cvat_video.zip` |
| Số track ID khác nhau trong `gt/gt.txt` (phải là 5) | 5 |
| Frame `outside` không có dòng trong `gt.txt` (đúng / sai) | Đúng, đã đối chiếu |
| Job đã completed trên CVAT máy cá nhân | Đã completed |

Dán phần tóm tắt in ra từ `src/check_submission.py`:

```text
=== Tóm tắt ===
Lỗi: 0   |   Cảnh báo: 1
Không có lỗi định dạng. Mở CVAT xem lại từng [CẢNH BÁO]; cảnh báo đúng ý bạn thì ghi lý do vào báo cáo.

Cảnh báo: Track 3 (P4) có 56 keyframe / 100 frame, vượt ngưỡng 50.
Tổng CVAT: 189 keyframe / 615 frame có mặt = 30.7 keyframe / 100 frame.
Đọc được 5 track từ annotations.xml.
```

## 6. Ba câu kết

1. Nếu được gán lại, bạn sẽ đặt keyframe khác ở đâu? Vì sao?

   Tôi sẽ rà lại các cụm keyframe dày của P4, nhất là khoảng frame 84–114 và 128–149. Tôi sẽ giữ keyframe ở chỗ box đổi vị trí hoặc kích thước rõ, nhưng bỏ những keyframe liền nhau nếu kiểm tra cho thấy nội suy không làm box trôi.

2. Có chỗ nào bạn không chắc "cùng ID hay ID mới"? Bạn đã quyết định và ghi chú thế nào?

   Ở P1, đoạn khuất hẳn frame 41–48 khiến tôi cân nhắc có tạo ID mới hay không. Vì chỉ khuất 8 frame (dưới ngưỡng 60), ngoại hình và hướng di chuyển khi hiện lại khớp, tôi giữ cùng ID P1.

3. Một lỗi ID trong job của bạn (nếu không còn sót, chọn lỗi đã sửa) có thể làm xe tự lái dự đoán sai chuyển động của người đó như thế nào? Lỗi đó ảnh hưởng MOTA hay IDF1 nhiều hơn?

   Nếu ID chuyển sang người khác, hệ thống có thể nối hai quỹ đạo thành một và dự đoán sai hướng hoặc vận tốc của cả hai người. ID switch ảnh hưởng trực tiếp hơn đến IDF1 vì chỉ số này đánh giá ghép đúng danh tính; MOTA cũng bị ảnh hưởng vì tính ID switch là lỗi.

## Bonus (nếu làm)

### B1 — Hai người đi sát

...

### B2 — So cách đặt keyframe

| Cách đặt | Số keyframe | Frame trôi nhất | Ghi chú |
|---|---:|---:|---|
| Đều mỗi 30 frame | | | |
| Theo chỗ đổi hướng | | | |

...

### B3 — So với tracker có sẵn

| Frame | Mã người | Tracker làm gì | Nhãn của bạn | Giải thích (đoán rồi sửa / ghép IoU / box score thấp / ngoại hình) |
|---:|---|---|---|---|
| | | | | |
| | | | | |

## 7. Tài liệu tham khảo và công cụ AI đã dùng

### Công cụ AI đã dùng

- Copilot SDK in VS Code.
- Mục đích sử dụng: Hỗ trợ diễn đạt và rà soát nội dung báo cáo, giải thích các chỉ số MOT và gợi ý cách trình bày quá trình tự kiểm tra.

