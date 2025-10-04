# Face Recognition using Eigenfaces
===================================


## Overview
------------

This project implements a **Face Recognition system** using the **Eigenfaces method**.  
Eigenfaces is a technique based on **Principal Component Analysis (PCA)**, which represents faces as a linear combination of principal components (Eigenfaces) instead of storing all pixels.  
It can recognize new faces by projecting them into the Eigenface space and comparing with the training dataset.

-----------------------------------------------------------------------------------------------

## Algorithim Steps
--------------------
1. **Collect Training Images**  
   Gather face images for each person and organize them in separate folders.  

2. **Convert Each Image to a Vector (Flatten)**  
   Transform each grayscale image into a 1D array.  

3. **Compute the Mean Face**  
   Calculate the average face across the training dataset.  

4. **Subtract the Mean Face**  
   Focus on differences between faces rather than overall characteristics.  

5. **Decompose to Find Principal Components**  
   - Apply **SVD** or **Eigen decomposition** on the covariance matrix.  
   - Eigenfaces correspond to the principal components representing face variations.  

6. **Select Top K Components**  
   Choose K eigenfaces that explain a desired confidence (e.g., 95%) of variance.  

7. **Project Training Images into Eigenface Space**  
   Calculate weights for each training image as linear combinations of top K eigenfaces.  

8. **Recognize New Faces**  
   - Subtract mean face from test image  
   - Project it into Eigenface space  
   - Compare weights with training weights using Euclidean distance  
   - Closest match predicts the person  

--------------------------------------------------------------------------------------------------

## Usage
----------

# Initialize recognizer
recognizer = FaceRecognizer(dataset_path=r"faces_dataset/train", confidence=0.95)  #folder having subfolders of faces

# Train the model
recognizer.train()

# Recognize a single test image
recognizer.recognize(test_img_path)



