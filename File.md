
Loading older messages…
How to add Dataset from pendrive in my code
You can use a dataset directly from your pendrive in Python or Jupyter Notebook by providing its folder path in your code. You don't need to download it again from the internet.

Let me explain step by step using your six Deep Learning practicals.

Step 1: Connect your pendrive
Insert your pendrive into your laptop.

Open This PC in Windows.

Check the pendrive drive letter (for example, E:).

Check the dataset folders inside it.

Example folder structure:

E:\
   DeepLearning_Datasets\
       MNIST\
       CIFAR10\
Step 2: Use the dataset path in your code
Practical 2, 3 and 4 – MNIST dataset
If your mam provides MNIST files in a folder, you can load them using:

import os

dataset_path = r"E:\DeepLearning_Datasets\MNIST"

print(os.listdir(dataset_path))

The exact loading code depends on the format of the files provided.

If the dataset is in CSV format:

import pandas as pd

data = pd.read_csv(
    r"E:\DeepLearning_Datasets\MNIST\mnist.csv"
)

print(data.head())

If it is in image folders:

import tensorflow as tf

dataset = tf.keras.utils.image_dataset_from_directory(
    r"E:\DeepLearning_Datasets\MNIST",
    image_size=(28, 28),
    color_mode="grayscale",
    batch_size=32
)

Practical 6 – CIFAR-10 dataset
If the dataset is provided as a CIFAR-10 Python batch archive, you can load it like this:

import pickle
import os

path = r"E:\DeepLearning_Datasets\CIFAR10"

with open(os.path.join(path, "data_batch_1"), "rb") as file:
    batch = pickle.load(file, encoding="bytes")

print(batch.keys())

This example assumes your pendrive contains the extracted CIFAR-10 Python batch files.

Step 3: Important precautions
Use r before Windows paths, such as r"E:\dataset".

Don't remove the pendrive while running your notebook.

Keep the pendrive drive letter unchanged.

If possible, copy the datasets to your laptop before the exam.

