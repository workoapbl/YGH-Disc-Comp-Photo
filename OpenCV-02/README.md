# Commonly Used Functions

This doc provides quick notes on commonly used OpenCV functions. This doc is not comprehensive. 

### Imports to Know
* `import cv2`: Imports OpenCV
* `import matplotlib.pyplot as plt`: Imports plotting library as plt
* `import numpy as np`: Imports Numpy as np

### OpenCV Basics
* `cv2.imread(image_path)`: Loads the image at image_path
* `cv2.imwrite(save_path, image)`: Saves the image to save_path
* `cv2.cvtColor(image, conversion)`: Converts the color channels of the image using a conversion map. Useful conversion maps: cv2.COLOR_BGR2RGB (BGR to RGB) and cv2.COLOR_RGB2BGR (RGB to BGR).

### Displaying using Matplotlib
```python
plt.imshow(image) # displays the image
plt.axis('off') # turns off axis on graph
plt.show() # shows the plot
```

### Numpy Basics
* `array[i, j]`: Gets element at row i and column j
* `array[i1:i2, j1:j2]`: Gets elements at rows i1 through i2 and columns j1 through j2
* `array[:, j1:j2]`: Gets elements from all rows in columns j1 through j2
* `array.astype(new_type)`: Converts elements to new_type. Common new_types: np.uint8, np.uint16, np.float32
*  `np.clip(array, lower, upper)`: Clips all elements in array to be between lower and upper.
* `np.dot(arr1, arr2)`: Computes the dot product between arr1 and arr2

### How to structure a Python project for this class
```python
# Start out with imports for needed libraries
import cv2
import matplotlib.pyplot as plt
import numpy as np 

# Set up any necessary functions
def example_function(image, value):
    """Write a helpful description for the function"""
    if value == 0:
        return image
    im = image.astype(np.uint16)
    im = im + value
    output = np.clip(im, 0, 255).astype(np.uint8)
    return output

# Load needed files
path = "images/path_to_image.jpg"
image = cv2.imread(path)

# Run any operations 
new_image = example_function(image, 50)

# Display image
plt.imshow(cv2.cvtColor(new_image, cv2.COLOR_BGR2RGB))
plt.axis('off')
plt.show()

# Save image
save_path = "images/updated_image.jpg"
cv2.imwrite(save_path, new_image)
```