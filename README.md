# Pre-Trained CNN Architecture for Indonesian Image Captioning using Transformer

> A comprehensive analysis of pre-trained CNN architectures for image captioning, using a Transformer model as the decoder. Experimentation uses the Flickr8k dataset with Indonesian captions, with key findings on encoder fine-tuning performance.

<div align="center">

<img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python" />
<img src="https://img.shields.io/badge/PyTorch-1.11-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" alt="PyTorch" />
<img src="https://img.shields.io/badge/Transformer-Decoder-EE4C2C?style=flat-square&logo=pytorch&logoColor=white" alt="Transformer" />
<img src="https://img.shields.io/badge/Dataset-Flickr8k-FF6B6B?style=flat-square&logo=flickr&logoColor=white" alt="Dataset" />
<img src="https://img.shields.io/badge/License-MIT-22B14C?style=flat-square&logo=opensourceinitiative&logoColor=white" alt="License" />
<img src="https://img.shields.io/badge/Platform-Google_Colab-F9AB00?style=flat-square&logo=googlecolab&logoColor=black" alt="Platform" />

</div>

---

## Features

| Feature | Description |
|---------|-------------|
| **Multiple CNN Encoders** | Supports VGG16, ResNet, GoogLeNet, InceptionV3, and other torchvision pre-trained models |
| **Transformer Decoder** | Multi-head attention with configurable layers and beam width |
| **Indonesian Captioning** | Trained on Flickr8k dataset with Indonesian annotations |
| **BLEU Evaluation** | Automated BLEU score computation for model evaluation |
| **Encoder Fine-tuning** | Optional fine-tuning of CNN encoder layers for improved performance |
| **Google Colab Ready** | Designed to run seamlessly in Google Colab with GPU support |

---

## Tech Stack

| Category | Technology |
|----------|-----------|
| Deep Learning | PyTorch 1.11.0 + Torchvision 0.12.0 |
| NLP | NLTK 3.10.0 (tokenization) |
| Visualization | Matplotlib 3.2.1 |
| Image Processing | Pillow 12.3.0 |
| Numerical | NumPy 1.18.2 |
| Progress | tqdm 4.45.0 |
| Evaluation | [pycocoevalcap](https://github.com/salaniz/pycocoevalcap) (COCO metrics) |

---

## Dataset

Download the Flickr8k dataset with Indonesian captions:

- **Images:** [Google Drive Folder](https://drive.google.com/drive/folders/10JDnoTQK-ZnE93lgp8D6iJajIPRLL5gq?usp=sharing)
- **Annotations:** [Google Drive Folder](https://drive.google.com/drive/folders/1QgSdzriDrvpKcUcooebmKl603qubkBbe?usp=share_link)

---

## Installation

### Prerequisites

- Python 3.8+
- Google Colab (recommended) or local GPU environment

### Setup

```bash
pip install -r requirements.txt
pip install "git+https://github.com/salaniz/pycocoevalcap.git"
```

### Vocabulary Generation

```bash
python vocab_builder.py
```

---

## Usage

### Training

Run inside Google Colab cells after vocabulary is generated (replace `x` with desired parameter values):

```bash
python train.py \
  --encoder-type vgg16 \
  --decoder-type transformer \
  --num-heads 1 \
  --num-tf-layers 3 \
  --beam-width 3 \
  --batch-size 64 \
  --batch-size-val 16 \
  --num-epochs 50 \
  --experiment-name nv_vgg16_tf_h1_l3_bs64_16_ep50
```

### Captioning

```bash
python caption.py --encoder-type vgg16 --experiment-name nv_vgg16_tf_h1_l3_bs64_16_ep50
```

### Evaluation

```bash
python eval.py --encoder-type vgg16 --experiment-name nv_vgg16_tf_h1_l3_bs64_16_ep50
```

---

## Project Structure

```
├── models.py           # Encoder (pre-trained CNN) + Transformer decoder
├── train.py            # Training pipeline with Flickr8k dataset
├── caption.py          # Image captioning inference
├── eval.py             # Evaluation metrics (BLEU, CIDEr, etc.)
├── bleu.py             # BLEU score computation
├── utils.py            # Utility functions
├── vocab_builder.py    # Vocabulary file generator
├── vocab.txt           # Pre-built vocabulary
├── requirements.txt    # Python dependencies
└── LICENSE             # License file
```

---

## Results

Results notebooks are available on [Google Colab](https://colab.research.google.com/drive/11jZAiZuLmOEq1VusyvAB0_7-XIgxQ-dg?usp=sharing).

---

## Security

| Package | Issue | Fix |
|---------|-------|-----|
| Pillow | [CVE-2026-59200](https://nvd.nist.gov/vuln/detail/cve-2026-59200) — Decompression Bomb DoS | Upgraded to 12.3.0 |
| NLTK | [CVE-2024-39705](https://nvd.nist.gov/vuln/detail/CVE-2024-39705) — Unsafe deserialization, SSRF, path traversal, ReDoS | Upgraded to 3.10.0 |

---

## License

This project includes a license file. See [LICENSE](LICENSE) for details.

## Developer

**Rifqi Mulyawan** — [rifqimulyawan.com](https://rifqimulyawan.com)
