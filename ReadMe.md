# 🚗 Vehicle & License Plate Detection Using YOLO11

A computer vision project for detecting **vehicles and license plates** in images and video using **YOLO11, Python, and OpenCV**. The project demonstrates an end-to-end object detection workflow, from dataset configuration and model training to evaluation and visual analysis of detection results.

---

## 📌 About the Project

Vehicle and license plate detection is an important application of **computer vision** and **deep learning**. It enables machines to automatically identify and localize objects of interest within images or video frames.

Traditional computer-vision approaches often rely on manually designed features and rule-based techniques. Modern object detection systems instead use deep neural networks to learn visual patterns directly from training data.

In this project, **YOLO11 (You Only Look Once)** is used as the object detection framework. YOLO treats detection as a single end-to-end problem, allowing the model to simultaneously determine:

* **What object is present**
* **Where the object is located**
* **How confident the model is about the prediction**

The project focuses on detecting vehicles and license plates and provides a foundation for applications such as intelligent transportation systems, traffic monitoring, automated vehicle analysis, and other vision-based systems.

---

## 🎯 Objective

The primary objective of this project is to build and evaluate a custom object detection model capable of identifying vehicles and license plates from visual input.

The workflow includes:

1. Preparing the dataset configuration
2. Training a YOLO11 object detection model
3. Evaluating model performance
4. Analyzing detection results
5. Supporting image and video-based inputs
6. Organizing the complete workflow into a reproducible project structure

---

## 🧠 What is Object Detection?

**Object detection** is a computer-vision task that combines two problems:

### 1. Classification

The model determines **what an object is**.

For example:

```text
Vehicle
License Plate
```

### 2. Localization

The model determines **where the object is** by predicting a bounding box around it.

A typical detection result can therefore be represented as:

```text
Object Class
     +
Bounding Box
     +
Confidence Score
```

For example:

```text
License Plate
Confidence: 0.94
Bounding Box: [x1, y1, x2, y2]
```

This makes object detection different from image classification, where the model generally predicts only the overall class of an image.

---

## ⚡ Why YOLO?

**YOLO (You Only Look Once)** is a family of real-time object detection models designed to perform detection efficiently in a single inference pipeline.

Instead of first generating possible regions and then classifying them separately, YOLO directly predicts object locations and classes from the input image.

This makes YOLO particularly useful for applications involving:

* Real-time video
* Traffic monitoring
* Vehicle detection
* License plate detection
* Surveillance systems
* Automated visual inspection

This project uses **YOLO11** for custom object detection.

---

## 🛠️ Technologies Used

| Technology           | Purpose                                |
| -------------------- | -------------------------------------- |
| **Python**           | Core programming language              |
| **YOLO11**           | Object detection model                 |
| **OpenCV (cv2)**     | Image and video processing             |
| **Jupyter Notebook** | Training and experimentation           |
| **Git & GitHub**     | Version control and project management |

---

## 🔬 Model Training

The YOLO11 model was trained for **13 epochs** using the custom dataset configuration defined in:

```text
config/data.yaml
```

The primary experimentation and training workflow is documented in:

```text
notebook/experiment.ipynb
```

The training process includes model initialization, dataset configuration, model training, and evaluation of the resulting detection performance.

---

## 📊 Model Performance

The trained model achieved the following evaluation metrics:

| Metric           |     Score |
| ---------------- | --------: |
| **mAP@0.5**      | **0.834** |
| **mAP@0.5:0.95** | **0.705** |
| **Precision**    | **0.837** |
| **Recall**       | **0.830** |

### Understanding the Metrics

#### mAP@0.5

**Mean Average Precision at IoU 0.5** measures detection performance using an Intersection over Union threshold of 0.5.

A score of:

```text
mAP@0.5 = 0.834
```

indicates strong detection performance under the IoU 0.5 criterion.

#### mAP@0.5:0.95

This metric evaluates the model across multiple IoU thresholds, from 0.5 to 0.95, making it a stricter measure of both detection and localization quality.

The model achieved:

```text
mAP@0.5:0.95 = 0.705
```

#### Precision

Precision measures how many of the objects predicted by the model were actually correct.

```text
Precision = 0.837
```

A higher precision means fewer false-positive detections.

#### Recall

Recall measures how many of the actual target objects were successfully detected.

```text
Recall = 0.830
```

A higher recall means the model is missing fewer relevant objects.

---

## 📁 Project Structure

```text
Vechicle_License_Detection/
│
├── config/
│   └── data.yaml
│
├── input/
│   ├── image/
│   └── video/
│
├── models/
│   ├── best.pt
│   └── yolo11.pt
│
├── notebook/
│   └── experiment.ipynb
│
├── output/
│   ├── images/
│   └── video/
│
└── requirement.txt

```

> Additional directories related to trained models, results, outputs, and other project components will be added as the project evolves.

### Directory Description

**`config/`**

Contains configuration files required for the object detection dataset and training workflow.

```text
config/data.yaml
```

**`input/image/`**

Contains image inputs used for testing or inference.

**`input/video/`**

Contains video inputs for video-based object detection.

**`notebook/`**

Contains the experimentation and model-training workflow.

```text
notebook/experiment.ipynb
```

---

## 🔄 Project Workflow

The overall workflow can be represented as:

```text
              Dataset
                 │
                 ▼
        Dataset Configuration
          config/data.yaml
                 │
                 ▼
          YOLO11 Training
                 │
                 ▼
          Model Evaluation
                 │
        ┌────────┴────────┐
        ▼                 ▼
      Images            Videos
        │                 │
        └────────┬────────┘
                 ▼
        Object Detection
                 │
                 ▼
       Vehicle / Plate Results
```

---

## 🖼️ Image Detection

The project supports image-based object detection.

Images placed inside:

```text
input/image/
```

can be used as input for testing the trained detection model.

The model processes the image and predicts the objects along with their bounding boxes and confidence scores.

---

## 🎥 Video Detection

The project also supports video-based detection.

Video files can be placed inside:

```text
input/video/
```

The detection pipeline can process video frames and identify the target objects throughout the video.

This makes the project suitable for exploring practical computer-vision applications beyond static images.

---

## 📈 Results & Evaluation

The training process generates various evaluation artifacts, which can be used to understand model performance.

Examples include:

* Precision curves
* Recall curves
* F1 curves
* Precision-Recall curves
* Confusion matrices
* Training results
* Validation predictions
* Training batch visualizations
* Trained model weights

These results help evaluate not only whether the model detects objects, but also how accurately and consistently it performs.

---

## 🚀 Upcoming Features

The project is being extended beyond object detection to build a more complete **vehicle analytics pipeline**.

### 🚗 Vehicle Tracking

* Assign a **unique tracking ID** to each detected vehicle
* Track vehicles consistently across consecutive video frames
* Visualize each vehicle's bounding box together with its live tracking ID

Example:

```text
Vehicle #12
Vehicle #27
Vehicle #31
```

### ⚡ Vehicle Speed Estimation

* Estimate the speed of tracked vehicles
* Display vehicle speed in **km/h**
* Calculate speed using vehicle movement across video frames

### 🔄 Complete Detection Pipeline

The planned end-to-end pipeline will combine multiple computer-vision tasks:

```text
Input Video
     │
     ▼
Object Detection
   (YOLO11)
     │
     ▼
Vehicle Tracking
(Unique Tracking IDs)
     │
     ▼
Bounding Box Visualization
+ Live Tracking IDs
     │
     ▼
Vehicle Speed Estimation
      (km/h)
```

The goal is to evolve the current project from a **vehicle and license plate detection system** into a more complete **Detection → Tracking → Speed Estimation pipeline**.

---

## 💡 Key Concepts Demonstrated

This project demonstrates practical implementation of several important computer-vision concepts:

* Object detection
* Bounding-box prediction
* Confidence-based detection
* YOLO architecture
* Custom model training
* Dataset configuration
* Model evaluation
* Precision and recall
* mAP-based evaluation
* Image processing with OpenCV
* Image-based inference
* Video-based inference
* Deep-learning experimentation

---

## 🚀 Future Improvements

Possible future improvements include:

* Increasing the size and diversity of the training dataset
* Experimenting with different YOLO11 model variants
* Increasing training epochs and comparing performance
* Improving detection of small license plates
* Optimizing inference speed
* Adding real-time camera detection
* Adding a dedicated inference script
* Adding automated result generation
* Exploring deployment of the trained model

---

## 📌 Project Status

The core object detection model has been trained and evaluated using YOLO11.

Current model performance:

```text
mAP@0.5       : 0.834
mAP@0.5:0.95  : 0.705
Precision     : 0.837
Recall        : 0.830
Epochs        : 13
```

The repository is being organized into separate configuration, input, experimentation, model, and result components to make the project easier to understand and extend.

---

## 👨‍💻 Author

**Vineet Bathla**

---

## ⭐ Summary

This project demonstrates how modern deep-learning-based object detection can be applied to **vehicle and license plate detection** using YOLO11.

It combines **Python, OpenCV, and YOLO11** to create a practical computer-vision workflow capable of working with both images and videos, while providing measurable model performance through standard object-detection evaluation metrics.
