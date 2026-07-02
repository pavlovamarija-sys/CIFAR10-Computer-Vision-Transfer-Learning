# CIFAR-10 Image Classification using Transfer Learning with ResNet50

## Project Overview

This project demonstrates an end-to-end Computer Vision workflow using **Transfer Learning** with a pretrained **ResNet50** model to classify images from the CIFAR-10 dataset.

The objective was to build an image classification model capable of recognizing one of ten object categories while demonstrating the complete deep learning pipeline, including data preprocessing, model building, transfer learning, fine-tuning, evaluation, and prediction analysis.

---

## Dataset

The project uses the **CIFAR-10** dataset, available through TensorFlow/Keras.

### Dataset Characteristics

- 60,000 RGB images
- Image size: **32 × 32 pixels**
- 10 object classes
- 50,000 training images
- 10,000 test images

For this project, only **10,000 training images** were used for training, while the complete test dataset was retained for evaluation.

### Classes

- Airplane
- Automobile
- Bird
- Cat
- Deer
- Dog
- Frog
- Horse
- Ship
- Truck

---

## Technologies Used

- Python
- TensorFlow / Keras
- NumPy
- Matplotlib
- Jupyter Notebook
- PyCharm
- Git & GitHub

---

## Project Workflow

### 1. Data Loading

The CIFAR-10 dataset was loaded directly from TensorFlow/Keras.

### 2. Data Exploration

Several sample images were visualized to verify the dataset and understand the different classes.

### 3. Data Preprocessing

The images were normalized by scaling pixel values from **0–255** to **0–1** before training.

---

## Model Architecture

The project uses **Transfer Learning** with a pretrained **ResNet50** model.

### Base Model

- ResNet50 pretrained on ImageNet
- `weights="imagenet"`
- `include_top=False`
- Input shape: `(32, 32, 3)`

### Custom Classification Head

- GlobalAveragePooling2D
- Dense (256 neurons, ReLU activation)
- Dropout (0.5)
- Dense (10 neurons, Softmax activation)

---

## Training Strategy

### Phase 1 – Training the Classification Head

During the first phase, the pretrained ResNet50 layers were frozen.

Only the custom classification head was trained.

- Epochs: **10**
- Learning rate: **0.001**

---

### Phase 2 – Fine-Tuning

The ResNet50 base model was then unfrozen and trained together with the custom classification head.

A much smaller learning rate was used to preserve the pretrained ImageNet features while adapting the network to the CIFAR-10 dataset.

- Epochs: **10**
- Learning rate: **0.00001**

---

## Results

| Metric | Result |
|--------|-------:|
| Phase 1 Validation Accuracy | ~20% |
| Phase 2 Validation Accuracy | **45.45%** |
| Final Test Accuracy | **44.39%** |
| Final Test Loss | **1.6701** |

---

## Prediction Analysis

The model correctly classified several object categories such as:

- Cats
- Frogs
- Ships
- Automobiles

Some visually similar classes were confused, including:

- Ship → Airplane
- Airplane → Ship
- Automobile → Truck
- Cat → Frog

These mistakes are expected because CIFAR-10 images have a very low resolution (32 × 32 pixels), making fine visual details difficult to distinguish.

---

## Key Learning Outcomes

This project demonstrates:

- Image preprocessing
- Transfer Learning
- Fine-tuning pretrained CNNs
- Model evaluation
- Prediction visualization
- Image classification using TensorFlow and Keras

---

## Future Improvements

Possible improvements include:

- Using `preprocess_input()` specifically designed for ResNet50
- Training on the complete 50,000-image training dataset
- Applying data augmentation
- Training for more epochs
- Hyperparameter tuning
- Comparing ResNet50 with other pretrained architectures such as EfficientNet or MobileNet

---

## Repository Structure

```
CIFAR10-Computer-Vision-Transfer-Learning/
│
├── notebooks/
│   └── cifar10_transfer_learning.ipynb
│
├── README.md
├── requirements.txt
└── .gitignore
```

---

## Author

**Marija Pavlova**

Computer Vision project completed as part of a Machine Learning / Deep Learning sprint, demonstrating transfer learning and fine-tuning using TensorFlow and Keras.