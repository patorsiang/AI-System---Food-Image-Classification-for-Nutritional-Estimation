# Food Image Classification for Nutritional Estimation

An AI/ML portfolio project exploring food image classification with the Food-101 dataset and transfer learning. The current repository focuses on image classification experiments; nutritional estimation is the intended downstream use case and still needs a completed implementation.

## Overview

This project investigates how a computer vision model can classify food images into food categories, which can later support nutritional estimation workflows such as mapping predicted food classes to calories or nutrient information.

The main experiment uses Food-101 image data and an EfficientNetV2B2 transfer-learning approach. The repository contains Jupyter notebooks, generated visual outputs, a saved model artifact tracked through Git LFS, and a classification report CSV.

Current scope:

- Food image classification
- Transfer learning with EfficientNetV2B2
- Training and fine-tuning experiments
- Evaluation with classification metrics
- Early groundwork for a nutritional-estimation system

Not yet complete:

- Full nutritional database integration
- Portion-size estimation
- Calorie/macronutrient prediction
- End-user inference app or API

## Why I Built This

I built this project to learn how an AI system can move from image classification toward a practical health or nutrition-related use case.

Food image classification is a useful starting point because the class prediction can become one input to a larger nutritional estimation pipeline. The project also gave me practice with:

- working with a large image dataset,
- transfer learning,
- model fine-tuning,
- training/validation/test workflows,
- classification reports,
- experiment comparison,
- and communicating ML results clearly.

## Problem Statement

Given an image of food, predict the most likely food category.

The longer-term product problem is:

> Can a food image classification model help estimate nutritional information by first identifying the food type, then connecting that prediction to nutrition data and portion-size estimation?

This repository currently addresses the first part: image classification. Nutritional estimation remains a TODO.

## Dataset

Dataset used:

- **Food-101**
- Loaded in notebooks through TensorFlow Datasets as `food101`
- 101 food classes
- Predefined training and validation/test split from TensorFlow Datasets

Evidence in the repo:

- `whole.ipynb` loads `dataset_name = "food101"`
- `colab.ipynb` loads `tfds.load(dataset_name, split="train", as_supervised=True)`
- Evaluation output in `res/classification_report_EfficientNetV2B2_20250311_040348.csv` reports 25,250 test/validation samples, which matches 101 classes with 250 samples per class.

TODO:

- Document exact train/validation split strategy used during each notebook run.
- Add dataset citation and license notes.
- Add a short data card describing class balance, image preprocessing, and known biases.

## Model Approach

The strongest documented run in this repo uses:

- EfficientNetV2B2
- Transfer learning
- Fine-tuning
- Sparse categorical cross-entropy
- Adam optimizer
- Accuracy as a training metric
- Classification report for final evaluation

The notebooks also show supporting workflow pieces:

- image resizing,
- normalization/preprocessing,
- data augmentation,
- batching,
- prefetching,
- early stopping,
- learning-rate reduction,
- classification report generation,
- confusion matrix generation,
- saved model export.

TODO:

- Add a clean experiment table listing every model attempted.
- Document image size and augmentation settings in one canonical place.
- Separate exploratory notebooks from the final reproducible notebook.

## Experiment Workflow

High-level workflow:

1. Load Food-101 from TensorFlow Datasets.
2. Inspect dataset metadata and class labels.
3. Preprocess images for EfficientNetV2B2.
4. Build a transfer-learning model.
5. Train the classification head.
6. Fine-tune selected model layers.
7. Evaluate on the held-out Food-101 validation/test split.
8. Generate a classification report and visual outputs.
9. Save model artifacts and result files.

Main files:

- `whole.ipynb` - main end-to-end experiment notebook for the documented EfficientNetV2B2 run
- `colab.ipynb` - Colab experiment notebook
- `compare.ipynb` - classification-report comparison work
- `diagram.ipynb` - EfficientNetV2B2 architecture visualization work
- `raptor.ipynb` - earlier/alternate experiment work
- `temp.ipynb` - scratch experiment notebook
- `res/classification_report_EfficientNetV2B2_20250311_040348.csv` - saved evaluation report
- `res/output.png` and `res/output2.png` - generated visual outputs
- `res/food101_EfficientNetV2B2_model_20250311_040348.h5` - Git LFS pointer for saved model artifact

## Metrics Used

The repository uses standard multi-class classification metrics:

- Accuracy
- Precision
- Recall
- F1-score
- Support
- Macro average
- Weighted average
- Confusion matrix
- Runtime/training time notes in notebook output

TODO:

- Add top-5 accuracy if it is used in a future run.
- Add inference latency and model size measurements for deployment readiness.
- Add per-class error analysis for similar-looking food classes.

## Results

Documented result file:

```text
res/classification_report_EfficientNetV2B2_20250311_040348.csv
```

Summary from the saved classification report:

| Metric | Value |
|---|---:|
| Accuracy | 0.8493 |
| Macro avg precision | 0.8492 |
| Macro avg recall | 0.8493 |
| Macro avg F1-score | 0.8488 |
| Weighted avg precision | 0.8492 |
| Weighted avg recall | 0.8493 |
| Weighted avg F1-score | 0.8488 |
| Evaluation support | 25,250 |

Notebook output also records:

- Initial training time: 10,135.96 seconds
- Classification report saved as `classification_report_EfficientNetV2B2_20250311_040348.csv`
- Model saved as `food101_EfficientNetV2B2_model_20250311_040348.h5`

TODO:

- Confirm whether the reported split should be called validation, test, or held-out evaluation in final write-up.
- Add final training/fine-tuning epoch counts in a concise experiment table.
- Add confusion matrix image or link to generated output.
- Add top-performing and weakest food classes.
- Add nutritional-estimation results once that pipeline exists.

## Tech Stack

- Python
- Jupyter Notebook / Google Colab
- TensorFlow
- Keras
- TensorFlow Datasets
- EfficientNetV2B2
- NumPy
- pandas
- scikit-learn
- Matplotlib
- Git LFS for model artifact tracking

TODO:

- Add a `requirements.txt` or `environment.yml` for reproducible setup.

## Project Structure

```text
.
|-- README.md
|-- whole.ipynb
|-- colab.ipynb
|-- compare.ipynb
|-- diagram.ipynb
|-- raptor.ipynb
|-- temp.ipynb
`-- res/
    |-- classification_report_EfficientNetV2B2_20250311_040348.csv
    |-- food101_EfficientNetV2B2_model_20250311_040348.h5
    |-- output.png
    `-- output2.png
```

## How to Run

The project is currently notebook-first.

Recommended path:

1. Open `whole.ipynb` in Google Colab or a local Jupyter environment.
2. Install/import the required ML libraries.
3. Load Food-101 using TensorFlow Datasets.
4. Run preprocessing cells.
5. Train or load the EfficientNetV2B2 model.
6. Generate evaluation outputs and classification reports.

Local setup outline:

```bash
git clone https://github.com/patorsiang/AI-System---Food-Image-Classification-for-Nutritional-Estimation.git
cd AI-System---Food-Image-Classification-for-Nutritional-Estimation
```

TODO:

- Add exact Python version.
- Add `requirements.txt`.
- Add a clean `notebooks/final.ipynb` or script-based training entry point.
- Add instructions for downloading Git LFS model artifacts.
- Add a lightweight inference example for one image.

## Demo / Screenshots

TODO: Add portfolio-ready visuals.

Available generated files:

- `res/output.png`
- `res/output2.png`

Suggested additions:

- Training/validation accuracy and loss chart
- Confusion matrix
- Example predictions with top predicted class
- Misclassification examples
- Nutritional-estimation mockup or future pipeline diagram

## What I Learned

- Transfer learning is an effective starting point for large image classification tasks.
- Food image classification is challenging because many classes look visually similar.
- A classification report is more useful than accuracy alone because class-level precision, recall, and F1-score reveal uneven performance.
- Fine-tuning can improve performance, but it needs careful learning-rate and overfitting control.
- Experiment notebooks become hard to maintain without a clear final notebook/script and environment file.
- Food recognition alone is not enough for nutritional estimation; portion size and nutrition database mapping are separate hard problems.

## Limitations

- Nutritional estimation is not fully implemented yet.
- No portion-size estimation is included.
- No nutrition database integration is included.
- The repo is notebook-heavy and not yet packaged as a reproducible training/inference pipeline.
- Exact environment dependencies are not documented in a requirements file.
- The saved model is tracked through Git LFS and may require Git LFS setup to download fully.
- Food-101 labels do not always map cleanly to precise nutritional values.
- Classification performance may vary on real-world food images outside Food-101.

## Future Improvements

- Add a reproducible environment file.
- Create a clean final notebook or Python training script.
- Add inference code for a single uploaded image.
- Add top-k predictions.
- Add model comparison table across architectures and hyperparameters.
- Add per-class analysis for best/worst performing food categories.
- Add confusion matrix visualization to the README.
- Connect food class predictions to a nutrition database.
- Add portion-size estimation or a user correction flow.
- Build a small demo UI or API for portfolio presentation.
- Add model-card style documentation covering intended use, limitations, and risks.

## Status

Status: classification experiment complete; portfolio documentation in progress; nutritional estimation remains TODO.

The current repository demonstrates an EfficientNetV2B2 Food-101 classification workflow with saved evaluation results. The next step is to make the experiment reproducible and extend it into a nutritional-estimation pipeline.
