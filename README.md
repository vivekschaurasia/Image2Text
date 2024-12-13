
# Image-to-Text Captioning System

This project implements an AI-based Image-to-Text system that generates descriptive captions for images by integrating advanced computer vision and natural language processing techniques. The system utilizes Xception (a pre-trained CNN) for image feature extraction and LSTM for caption generation.

---

## Features

- Extracts high-level features from images using a pre-trained Xception model.
- Generates accurate and contextually relevant captions with LSTM.
- Supports BLEU score evaluation for caption quality.
- Modular implementation for easy extensibility.

---

## Dataset

This project uses the **Flickr8k** dataset, which includes:
- **8,000 images** with **5 captions per image**.

### Dataset Structure:
```
Dataset/
├── Images/              # Folder containing image files
├── captions.txt         # Text file with image-caption mappings
```


## Installation

### Prerequisites
- Python 3.7+
- Pip package manager



### Install Dependencies
Install the required Python packages:
```bash
pip install -r requirements.txt
```

---

## Usage

### 1. Set Up the Dataset
- Place the dataset under the `Dataset/` folder as described in the dataset structure.
- Ensure `captions.txt` contains the mappings of image filenames to their captions.

### 2. Train the Model
Run the script to preprocess the data, extract features, and train the model:
```bash
python Untitled-1.py
```
- Default parameters:
  - Epochs: 13
  - Batch size: 32

### 3. Generate Captions
Use the `generate_caption` function in the script to predict captions for images:
```python
lst, pred = generate_caption(model, "1096165011_cc5eb16aa6", image_directory, mapping, featuresx, tokenizer, max_length)
```

### 4. Evaluate the Model
Evaluate the performance using BLEU scores:
```python
from nltk.translate.bleu_score import corpus_bleu
actual, predicted = list(), list()
bleu_score = corpus_bleu(actual, predicted)
print(f"BLEU Score: {bleu_score}")
```

---

## Results

### Example Output:
- **Generated Caption**: "A boys is smiling underwater."

### BLEU Score:
- Achieved BLEU score: `0.066` .


## Project Structure

```
.
├── Untitled-1.py          # Main script for training and testing
├── Dataset/               # Contains images and captions.txt
├── requirements.txt       # Python dependencies
├── README.md              # Project documentation
```

---

## Limitations

- **Subjective Captions**: BLEU scores can be low due to the subjective nature of captions.
- **Complex Scenes**: Model struggles with images containing multiple objects or intricate details.

---

## Future Enhancements

1. **Advanced Architectures**:
   - Experiment with Vision Transformers (ViT) or GPT-based models for improved caption generation.
2. **Larger Datasets**:
   - Incorporate datasets like COCO or Visual Genome for better generalization.
3. **Multilingual Captioning**:
   - Extend functionality to support captions in multiple languages.

---


## Acknowledgements

- **Dataset**: [Flickr8k Dataset](https://www.kaggle.com/datasets/adityajn105/flickr8k)
- **Xception Model**: Keras Applications
- **References**:
  - [Understanding BLEU Score](https://www.aclweb.org/anthology/P02-1040/)
  - [Understanding LSTMs](https://colah.github.io/posts/2015-08-Understanding-LSTMs/)
