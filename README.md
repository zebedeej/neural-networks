# Home Assignment 1: Tensor Reshaping and Neural Network Operations

This repository contains the work completed for  Assignment 1. The assignment uses TensorFlow and Python to demonstrate tensor operations, loss functions, neural network optimization, MNIST classification, and TensorBoard logging.

## Contents

The notebook includes the following tasks:

1. Tensor reshaping and broadcasting
2. Implementation and comparison of loss functions
3. MNIST neural network training using Adam and SGD
4. Neural network training with TensorBoard logging
5. Questions about training and validation accuracy, overfitting, and the effect of increasing epochs

## Technologies Used

- Python 3
- TensorFlow
- Matplotlib
- Jupyter Notebook
- TensorBoard

## Tasks

### 1. Tensor Reshaping and Operations

A random TensorFlow tensor with shape `(4, 6)` is created.

The notebook then:

- Finds the rank of the tensor
- Finds the tensor shape
- Reshapes the tensor from `(4, 6)` to `(2, 3, 4)`
- Transposes it to `(3, 2, 4)`
- Creates a smaller tensor with shape `(1, 4)`
- Uses TensorFlow broadcasting to add the smaller tensor to the transposed tensor

The final broadcasted result has shape `(3, 2, 4)`.

### 2. Loss Functions

The notebook compares two loss functions:

- Mean Squared Error (MSE)
- Categorical Cross Entropy (CCE)

Two sets of predictions are compared against the same true labels.

The recorded results are:

| Loss Function | Original | Changed |
|---|---:|---:|
| MSE | 0.0333 | 0.0833 |
| Categorical Cross Entropy | 0.2899 | 0.5108 |

The results show that both loss values increase when the predictions become less accurate.

### 3. MNIST Model: Adam vs SGD

The MNIST handwritten digit dataset is loaded using TensorFlow.

The images are normalized by dividing pixel values by `255.0`.

Two neural networks with the same architecture are trained:

- Flatten layer for the `28 x 28` images
- Dense layer with 128 neurons and ReLU activation
- Dense output layer with 10 neurons and softmax activation

The only difference between the two models is the optimizer:

- Adam
- SGD

Both models are trained for 5 epochs with 20% of the training data used for validation.

#### Recorded Results

The Adam model reached a training accuracy of approximately **98.47%** and validation accuracy of approximately **97.39%** after 5 epochs.

The SGD model reached a training accuracy of approximately **92.69%** and validation accuracy of approximately **93.21%** after 5 epochs.

Based on these results, Adam achieved higher accuracy and lower loss than SGD in this experiment.

### 4. TensorBoard Logging

A second MNIST neural network is trained using the Adam optimizer and TensorBoard logging.

The training configuration includes:

- 5 epochs
- 20% validation split
- Sparse categorical cross entropy loss
- Accuracy as the evaluation metric
- TensorBoard logs saved under `logs/fit/`

The final recorded validation accuracy was approximately **97.41%**.

The notebook also attempts to launch TensorBoard using the `logs/fit/` directory. In the recorded run, TensorBoard could not be launched because the TensorBoard executable was not available in the environment.

## Questions and Observations

### Training and Validation Accuracy

Training accuracy generally increases as the model learns from the training data. Validation accuracy also increases when the model improves on data that was not used for training.

When the training and validation curves remain relatively close, it indicates that the model is generalizing reasonably well.

### Detecting Overfitting with TensorBoard

TensorBoard can be used to compare training and validation accuracy and loss.

A possible sign of overfitting is:

- Training accuracy continues to increase
- Validation accuracy stops improving or decreases
- Training loss continues to decrease
- Validation loss starts to increase

This indicates that the model may be learning the training data too closely instead of learning patterns that generalize to unseen data.

### Effect of Increasing Epochs

Increasing the number of epochs gives the neural network more opportunities to learn from the training data.

Initially, additional epochs can improve performance. However, training for too many epochs can cause overfitting. In that situation, training accuracy may continue to improve while validation accuracy gets worse.

## Project Structure

```text
.
├── Home Assignment 1. .ipynb
├── README.md
└── logs/
    └── fit/
```

The `logs/fit/` directory is used for TensorBoard training logs when the notebook is executed.

## How to Run

1. Install Python 3.
2. Install the required packages:

```bash
pip install tensorflow matplotlib jupyter tensorboard
```

3. Open the notebook:

```bash
jupyter notebook "Home Assignment 1. .ipynb"
```

4. Run the notebook cells from top to bottom.

5. To view TensorBoard after generating the logs, run:

```bash
tensorboard --logdir logs/fit/
```

Then open the local TensorBoard address shown in the terminal.

## Notes

The random tensor values and neural network results can vary slightly when the notebook is executed again because model training and random tensor generation can depend on random initialization and other runtime factors.

The results and observations in this README are based on the outputs recorded in the submitted notebook.
