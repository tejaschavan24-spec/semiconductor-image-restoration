# Semiconductor Image Restoration

Deep learning based restoration and 2× super-resolution of noisy semiconductor microscopy images.

## 📌 Project Overview

This project focuses on reconstructing high-resolution semiconductor microscopy images from noisy, low-resolution observations using deep learning.

The model takes a **128×128 noisy grayscale image** as input and produces a **256×256 restored image**.

### Input → Output

- Input: NoisyLR image — `128×128`
- Output: Restored image — `256×256`
- Ground Truth: `256×256`
- Image type: Grayscale

## 📊 Dataset

The dataset contains paired noisy low-resolution and high-resolution ground-truth images.

- Total image pairs: **3,200**
- Training images: **2,880**
- Validation images: **320**
- NoisyLR resolution: **128×128**
- Ground Truth resolution: **256×256**

The dataset itself is not included in this repository due to its size.

## 🧠 Model Architecture

The baseline restoration network uses:

- Convolutional feature extraction
- Residual blocks
- 64 feature channels
- 8 residual blocks
- PixelShuffle ×2 upsampling
- Sigmoid output layer

The network was implemented using **PyTorch** and trained using GPU acceleration.

## 🧪 Models Evaluated

Several model configurations were trained and compared.

### Baseline

Residual restoration network trained primarily using L1 loss.

### Model 2

Baseline architecture with an SSIM-oriented loss component.

### Model 3

Baseline architecture incorporating a gradient-based loss component.

### Model 4

Extended training/optimization configuration.

## 📈 Results

| Model | PSNR (dB) | SSIM |
|---|---:|---:|
| Baseline | 25.8306 | 0.7266 |
| Model 2 | 25.8719 | 0.7437 |
| Model 3 | **25.9592** | 0.7437 |
| Model 4 | 25.6538 | **0.7541** |

### Best Results

🏆 **Best PSNR:** Model 3 — **25.9592 dB**

🏆 **Best SSIM:** Model 4 — **0.7541**

Model 3 produced the highest PSNR, while Model 4 achieved the highest SSIM, showing that the two metrics capture different aspects of restoration quality.

## 🖼️ Qualitative Results

Comparison between the noisy input, restored outputs, and ground truth images is provided in the `results/` directory.

## 💻 Hardware

Training was performed using:

- NVIDIA Tesla T4 GPU
- CUDA
- Google Colab

The models are implemented in PyTorch and are compatible with NVIDIA CUDA-enabled GPUs.

## 🛠️ Technologies

- Python
- PyTorch
- NumPy
- TorchMetrics
- Matplotlib
- Google Colab

## 📁 Repository Structure

```text
semiconductor-image-restoration/
│
├── Semiconductor_Image_Restoration.ipynb
├── README.md
├── requirements.txt
│
└── results/
    ├── psnr_comparison.png
    ├── ssim_comparison.png
    └── qualitative_comparison.png
