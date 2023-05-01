# Hand Detector using Mediapipe

This is a Python-based hand detector that uses the Mediapipe library. The library helps to export hand landmarks in pixel format and also provides additional functionalities such as finding the number of fingers raised and the distance between two fingers. The output also includes the bounding box information of the hand found.

## Installation

To use this hand detector, you need to have Python 3 installed on your machine. Then, follow the instructions below:

1. Clone this repository to your local machine using the command below:

```bash
git clone https://github.com/<username>/hand-detector.git
```

2. Install the required dependencies using the following command:

```bash
pip install -r requirements.txt
```

## Usage

To use the hand detector, you need to create an instance of the `HandDetector` class and call the `findHands` method on an image. Below is an example:

```python
import cv2
from hand_detector import HandDetector

# Create instance of the HandDetector class
detector = HandDetector()

# Load an image
img = cv2.imread("test.jpg")

# Find hands in the image
hands, img = detector.findHands(img, draw=True)

# Display the image with the detected hands
cv2.imshow("Image", img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

You can also find the number of fingers raised and the distance between two fingers using the `fingersUp` and `findDistance` methods, respectively. Below are examples:

```python
# Find fingers raised
fingers = detector.fingersUp(hands[0])
print(fingers)  # Prints a list of which fingers are up

# Find distance between two fingers
distance = detector.findDistance(hands[0]["lmList"][4], hands[0]["lmList"][8])
print(distance)  # Prints the distance in pixels
```

## Options

The `HandDetector` class accepts several parameters that allow you to adjust the detection settings. These parameters are:

- `mode`: In static mode, detection is done on each image: slower (default is False)
- `maxHands`: Maximum number of hands to detect (default is 2)
- `detectionCon`: Minimum Detection Confidence Threshold (default is 0.5)
- `minTrackCon`: Minimum Tracking Confidence Threshold (default is 0.5)

You can adjust these parameters when creating an instance of the `HandDetector` class. Here is an example:

```python
# Create instance of the HandDetector class with custom settings
detector = HandDetector(mode=True, maxHands=1, detectionCon=0.7, minTrackCon=0.7)
``'
