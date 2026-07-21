# Do Machines Hallucinate Faces Like We Do? A Comparative Study of Human and Algorithmic Pareidolia

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/)
[![Jupyter Notebook](https://img.shields.io/badge/Notebook-Jupyter-orange.svg)](https://jupyter.org/)
[![Course Project](https://img.shields.io/badge/Course-PSYCH--UA%20300--011-purple.svg)](#)

## 📌 Authors & Affiliation
* **Sachi Sharma**, **Atlas Robinson**, **Alexa Yang**, **Catherine Lin**
* **Course**: PSYCH-UA 300-011: Special Topics Psychology: Computational Cognitive Science[cite: 2]
* **Instructors**: Todd Gureckis and Mark Ho[cite: 2]
* **Date**: May 11, 2026[cite: 2]

---

## 📖 Abstract
Pareidolia—the perception of illusory faces in non-face stimuli—reveals a core asymmetry in human visual processing: biological vision prioritizes avoiding false negatives for face detection, even at the cost of frequent false alarms[cite: 2]. To test whether algorithmic face classifiers exhibit a similar bias, we compared four classifiers of increasing complexity (**kNN**, **Softmax**, **SVM**, and a **Two-Layer Neural Network**) against human participants ($n=5$) completing a 2-block continuous rating task on pareidolia stimuli[cite: 2].

Our findings reveal that while standard classifiers achieve high accuracy on true faces and objects, they **rarely classify pareidolia stimuli as faces** (false-face detection rate $\le 12.3\%$)[cite: 2]. In contrast, human participants exhibit a low mean accuracy ($\approx 39\%$) on pareidolia stimuli due to severe perceptual bias[cite: 2]. This highlights that human face pareidolia arises from complex top-down cognitive and evolutionary mechanics rather than basic visual pattern recognition[cite: 2].

---

## 📂 Repository Contents

* `pareidolia_study.ipynb`: The primary Jupyter Notebook containing data preprocessing, model implementations (kNN, Softmax HOG, ReLU Neural Net), evaluation metrics, and human comparison plots[cite: 2].
* `CCS Final Paper (2).pdf`: Full written research paper detailing our theoretical background, behavioral experiment design, and cognitive science implications[cite: 2].

---

## 🔬 Methodology Overview

### Data & Preprocessing Pipeline
* **Dataset ($N=300$)**: 150 faces (AT&T Face Database) + 150 everyday objects (CIFAR-10) [75/25 Train/Val Split][cite: 2].
* **Preprocessing**: Standardized to single-channel grayscale ($32 \times 32$ resolution, RGB channel std variance $= 0.0$), zero-centered via training mean subtraction[cite: 2].
* **Feature Extraction**:
  * **Raw Pixels**: $3072$-dimensional flattened vectors ($32 \times 32 \times 3$)[cite: 2].
  * **HOG Features**: Histogram of Oriented Gradients (9 orientations, $8 \times 8$ cell size) producing a $144$-dimensional feature vector[cite: 2].

### Classifiers
1. **$k$-Nearest Neighbor ($k\text{NN}$)**: Baseline distance metric using vectorized $L_2$ Euclidean distance[cite: 2].
2. **Linear Classifiers**: **Softmax Classifier** & **Structured Support Vector Machine (SVM)** optimized via grid-search hyperparameter tuning[cite: 2].
3. **Two-Layer Neural Network**: Fully-connected network ($100$ hidden units, **ReLU** activation) trained via backpropagation[cite: 2].

---

## 📊 Key Results

### 1. Model Performance (Validation Set)
| Model | Feature Vector | Accuracy | Latency (ms) | Avg Confidence | F1-Score | Precision | Recall |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **kNN** | Raw Pixels | **97.00%** | 0.0812 | N/A | **0.97** | 0.94 | **1.00** |
| **Softmax** | HOG Features | 95.50% | **0.0026** | 77.8% | 0.95 | **0.96** | 0.95 |
| **ReLU Net** | Raw Pixels | 88.00% | 0.0375 | **97.3%** | 0.87 | 0.95 | 0.80 |

### 2. Human vs. Model Pareidolia Sensitivity
| Agent / Model | Correctly Identified Pareidolia as Non-Face (Accuracy) |
| :--- | :---: |
| **Human Participants** ($n=5$) | **39.0%** *(High Pareidolia Sensitivity)* |
| **kNN Classifier** | **87.7%** |
| **Softmax (HOG)** | **87.7%** |
| **Two-Layer ReLU Net** | **95.4%** *(Low Pareidolia Sensitivity)* |

> **Key Takeaway**: Standard artificial classifiers treat pareidolia images strictly as non-faces (objects), whereas human visual processing exhibits a strong bias to hallucinate faces in ambiguous non-face stimuli[cite: 2].

---

## 📚 Key References
* **Akdeniz, G., Toker, S., & Atli, I. (2018).** Neural mechanisms underlying visual pareidolia processing: An fMRI study. *Pakistan Journal of Medical Sciences*, 34(6), 1560–1566[cite: 2].
* **CS231n Course. (2024).** *Assignment 1: Image Classification, kNN, SVM, Softmax, Fully Connected Neural Network*. Stanford University[cite: 2].
* **Gupta, P., & Dobs, K. (2025).** Human-like face pareidolia emerges in deep neural networks optimized for face and object recognition. *PLoS Computational Biology*, 21(1), e1012751[cite: 2].
* **Taubert, J., et al. (2017).** Face pareidolia in the rhesus monkey. *Current Biology*, 27(16), 2505–2509[cite: 2].
* **Wardle, S. G., et al. (2020).** Rapid and dynamic processing of face pareidolia in the human brain. *Nature Communications*, 11, 4518[cite: 2].
