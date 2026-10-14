# M6 Facial Expression Recognition Model

Mô hình TensorFlow Lite dùng để phân loại biểu cảm khuôn mặt, được tối ưu để chuẩn bị triển khai trên Raspberry Pi.

## Kết quả

- Accuracy: **77,24%**
- Macro F1: **72,90%**
- Top-2 Accuracy: **92,34%**
- Tập kiểm tra: **2.834 ảnh RAF-DB**
- Số ảnh dự đoán đúng: **2.189 ảnh**
- Kích thước mô hình TFLite: **4,33 MB**

## Các lớp biểu cảm

Thứ tự đầu ra của mô hình:

```python
[
    "angry",
    "happy",
    "neutral",
    "sad",
    "surprise"
]
```

Không được thay đổi thứ tự các lớp khi triển khai.

## Tệp mô hình

- `m6_float32.tflite`: mô hình TensorFlow Lite Float32.
- `m6_class_names.json`: danh sách và thứ tự các lớp.

## Đầu vào và đầu ra

- Input shape: `1 × 160 × 160 × 3`
- Input dtype: `float32`
- Không gian màu: `RGB`
- Output shape: `1 × 5`
- Output: xác suất của năm lớp biểu cảm.

Quy trình tiền xử lý:

```text
Ảnh camera
→ YuNet phát hiện khuôn mặt
→ Cắt vùng khuôn mặt
→ Chuyển BGR sang RGB
→ Resize về 160 × 160
→ Chuyển sang Float32
→ M6 TensorFlow Lite dự đoán
