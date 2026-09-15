# EX 10 - Opening and Closing Operations Using OpenCV

## Aim

To write a Python program using OpenCV to perform morphological Opening and Closing operations on an image.

The program performs the following operations:

* Morphological Opening
* Morphological Closing

## Software Used

* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

## Algorithm

### Step 1:

Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:

Create or load an input image containing foreground objects.

### Step 3:

Display the original image.

### Step 4:

Create a structuring element (kernel) of suitable size.

### Step 5: Opening Operation

* Apply the Opening operation using the structuring element.
* Opening consists of Erosion followed by Dilation.
* Remove small foreground noises while preserving the shape of larger objects.
* Display the opened image.

### Step 6: Closing Operation

* Apply the Closing operation using the structuring element.
* Closing consists of Dilation followed by Erosion.
* Fill small holes and gaps within foreground objects.
* Display the closed image.

### Step 7:

Compare the original, opened, and closed images.

## Program

```python
# Name: C J Rohit
# Reg No: 212224243005

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load the input image
image_path = "JANA JAVA.jpg"
image = cv2.imread(image_path)

if image is None:
    raise FileNotFoundError("Input image not found.")

# Convert the image to grayscale
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

# Convert grayscale image to binary image
_, binary = cv2.threshold(gray, 127, 255, cv2.THRESH_BINARY)

# Create a structuring element
kernel = np.ones((5, 5), np.uint8)

# Opening: Erosion followed by Dilation
opened = cv2.morphologyEx(binary, cv2.MORPH_OPEN, kernel)

# Closing: Dilation followed by Erosion
closed = cv2.morphologyEx(binary, cv2.MORPH_CLOSE, kernel)

# Convert original image from BGR to RGB
original_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)

# Display the images
plt.figure(figsize=(12, 8))

plt.subplot(2, 2, 1)
plt.imshow(original_rgb)
plt.title("Original Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.imshow(binary, cmap="gray")
plt.title("Binary Image")
plt.axis("off")

plt.subplot(2, 2, 3)
plt.imshow(opened, cmap="gray")
plt.title("Opening Operation")
plt.axis("off")

plt.subplot(2, 2, 4)
plt.imshow(closed, cmap="gray")
plt.title("Closing Operation")
plt.axis("off")

plt.tight_layout()
plt.show()
```

## Developed By

**Name:** C J Rohit

**Register No:** 212224243005

## Output


### Original Image
<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/97c838b8-de3d-46f3-8fd1-0a1f8605910a" />
<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/892729c3-3bf8-46e2-83e0-9804afcc2ac7" />

* The input image is displayed.
* The image serves as the source for morphological processing.

### Opening Operation

* The binary image is processed using Opening.
* Opening consists of Erosion followed by Dilation.
* Small foreground noise is removed.
* Thin protrusions and isolated pixels are eliminated.
* Object boundaries become smoother.

### Closing Operation

* The binary image is processed using Closing.
* Closing consists of Dilation followed by Erosion.
* Small holes and gaps inside objects are filled.
* Broken regions may be connected.
* Object boundaries become more continuous.

## Applications

### Opening

* Noise removal in binary images.
* Separation of connected objects.
* Preprocessing for object detection.

### Closing

* Filling small holes in objects.
* Connecting nearby components.
* Enhancing segmented regions.

## Advantages

### Opening

* Removes unwanted foreground noise.
* Preserves major object structures.
* Improves segmentation quality.

### Closing

* Restores object continuity.
* Eliminates small background gaps.
* Improves object representation.

## Result

Thus, the morphological operations **Opening** and **Closing** are successfully implemented using OpenCV.
