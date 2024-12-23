# Road Damage Detection Using YOLOv8

## Overview
This project focuses on detecting road damages such as cracks, potholes, and other surface deformities using **YOLOv8**, a state-of-the-art object detection model. The goal is to provide an efficient and scalable solution to monitor road conditions and support maintenance operations.

---

## Features
- **Real-time Damage Detection**: Utilize YOLOv8 to detect road damages in real-time.
- **High Accuracy**: Leverages the advanced architecture of YOLOv8 for accurate predictions.
- **Custom Dataset**: Trained on a road damage dataset for specific types of damages like cracks, potholes, etc.
- **Scalable Solution**: Can be deployed on edge devices, drones, or integrated into traffic monitoring systems.

---

## Installation

### Prerequisites
Ensure you have the following installed:
- Python (>= 3.8)
- pip
- GPU with CUDA (optional but recommended for faster inference)


### Install Dependencies
```bash
pip install -r requirements.txt
```

### Additional Setup
- Install `ultralytics` for YOLOv8:
```bash
pip install ultralytics
```
- Verify installation:
```bash
yolo --version
```

---

## Dataset

### Dataset Preparation
1. Download the **Road Damage Dataset** or any custom dataset.
2. Organize the dataset in the YOLO format:
   ```
   dataset/
   ├── train/
   │   ├── images/      # Training images
   │   └── labels/      # Corresponding labels in YOLO format
   └── val/
       ├── images/        # Validation images
       └── labels/        # Corresponding labels in YOLO format
   ```
3. Update the dataset path in `data.yaml`:
   ```yaml
   train: dataset/train/images
   val: dataset/val/images

   nc: 3  # Number of classes
   names: ['all', 'Repair', 'alligator cracks', 'longitudinal cracks', 'potholes', 'transverse cracks']  # Class names
   ```

---

## Training

To train the YOLOv8 model on your dataset:
```bash
yolo task=detect mode=train model=yolov8n.pt data=data.yaml epochs=50 imgsz=640
```
- **Parameters**:
  - `model`: Pre-trained YOLOv8 model (e.g., `yolov8n.pt`, `yolov8s.pt`)
  - `epochs`: Number of training epochs
  - `imgsz`: Image size for training

---

## Inference

Run inference on images, videos, or live streams:
```bash
yolo task=detect mode=predict model=path/to/best.pt source=path/to/input
```
- **Parameters**:
  - `model`: Path to the trained model (e.g., `runs/detect/train/weights/best.pt`)
  - `source`: Path to the input (image, video, or folder of images)

Example:
```bash
yolo task=detect mode=predict model=best.pt source=sample.jpg
```

---

## Evaluation
Evaluate the model performance on the validation set:
```bash
yolo task=detect mode=val model=path/to/best.pt data=data.yaml
```

---

## Deployment

### Streamlit Web App
Deploy a web-based demo using **Streamlit**:
```bash
streamlit run app.py
```

### Flask API
Run a Flask server for integration with other systems:
```bash
python app.py
```

---

## Results
### Sample Output
- **Bounding Boxes**: Visualize detected road damages with confidence scores.
- **Metrics**: Display metrics like mAP, precision, recall, and F1-score.

---

## Folder Structure
```
road-damage-detection-yolov8/
├── dataset/               # Dataset folder
├── runs/                  # Training runs
├── models/                # YOLOv8 models
├── scripts/               # Utility scripts
├── app.py                 # Web/Flask app
├── requirements.txt       # Dependencies
├── data.yaml              # Dataset configuration
└── README.md              # Project documentation
```

---

## Contributing
Contributions are welcome! Feel free to:
- Submit pull requests
- Report issues
- Suggest enhancements

---

## License
This project is licensed under the MIT License. See `LICENSE` for details.

---

## Acknowledgments
- [Ultralytics YOLOv8](https://github.com/ultralytics/ultralytics)
- Public Road Damage Datasets

---


