# Báo cáo cá nhân — Day 01: Lọc tin nhắn rác bằng ML, DL, Embedding và LLM

> Đổi tên file này thành `MSSV_HoTen.md` của bạn, ví dụ `2A20260000_NguyenVanAn.md`, rồi điền từng mục. Xoá các dòng hướng dẫn in nghiêng khi xong.

- **MSSV: 2A202603821**
- **Họ và tên: Trần Thành Vinh**
- **SEED** 5629:

## 1. Bằng chứng

| Tệp | Có? |
| --- | --- |
| [`day01_lab.ipynb`](day01_lab.ipynb) — notebook đã chạy, còn output | yes |
| [`lab1_report.json`](lab1_report.json) — do ô "Báo cáo cuối" sinh ra | yes |
| [`hand_calc.jpg`](hand_calc.jpg) — ảnh tính tay có các bước | yes |

## 2. Kết quả chính

*Chép bảng so sánh cuối Phần 5 (F1 test, F1 SUB 40, p95 ms/tin, USD/1k tin) của chính bạn.*

                                 precision  recall  F1 (test)  F1 (SUB 40)  \
1. BoW + LogReg (tự code)            1.000   0.795      0.886        0.824   
2. BoW + MLP (deep learning)         0.952   0.893      0.922        0.923   
3a. Encoder (MiniLM) + kNN           0.875   0.938      0.905        0.923   
3b. Encoder (MiniLM) + LogReg        0.990   0.929      0.959        0.895   
3c. Encoder (MiniLM) + MLP head      0.991   0.938      0.963        0.919   

                                 train (s)  tin/s (cả lô)  p50 ms/tin  \
1. BoW + LogReg (tự code)            1.734      40394.669       0.052   
2. BoW + MLP (deep learning)         3.783      49568.232       0.161   
3a. Encoder (MiniLM) + kNN          35.266         39.022      73.038   
3b. Encoder (MiniLM) + LogReg       35.604         73.661      19.113   
3c. Encoder (MiniLM) + MLP head     36.306         76.880      15.879   

                                 p95 ms/tin  USD / 1k tin  
1. BoW + LogReg (tự code)             0.072           0.0  
2. BoW + MLP (deep learning)          0.255           0.0  
3a. Encoder (MiniLM) + kNN          123.923           0.0  
3b. Encoder (MiniLM) + LogReg        29.672           0.0  
3c. Encoder (MiniLM) + MLP head      21.532           0.0  
• Hàng LLM chỉ đo trên SUB (40 tin) → so sánh chất lượng công bằng bằng cột 'F1 (SUB 40)'.
• SUB chỉ 40 tin: 1 tin sai đổi F1 vài điểm. Chênh < ~0.05 F1 coi như HOÀ — đừng xếp hạng theo số lẻ.
• Inference đo TỪ VĂN BẢN THÔ → NHÃN (gồm cả vectorize / encode). p50/p95 = gọi từng tin một, như một request thật.
• train (s) của 3a/3b/3c = thời gian encoder MiniLM encode tập train (+ train đầu LogReg / MLP); LLM = 0 vì không train. Số đo phụ thuộc CPU/GPU của Colab.

## 3. Dự đoán và thực tế

*Chọn 3 dự đoán `predict(...)` lệch nhiều nhất so với kết quả. Mỗi cái: bạn đoán gì, ra gì, vì sao lệch.*

## 4. Phân tích 50 case khó

*Model nào tụt nhiều nhất, ở nhóm case nào? Nêu 2 case cụ thể và cơ chế khiến model sai.*

## 5. Thử thách cá nhân

*Đề theo SEED của bạn, cách làm, kết quả, giải thích.*

## 6. Phương án cho sản phẩm thật

*Với yêu cầu p95 < 50 ms/tin cho 10 triệu SMS/ngày: chọn phương án nào, dẫn số liệu nào, chấp nhận đánh đổi gì.*

## 7. AI log và điều đã học

*Mỗi lần dùng AI: hỏi gì, nhận gì, bạn sửa gì. Sau đó 2–3 câu: điều bạn hiểu ra hôm nay mà trước đó chưa hiểu.*
