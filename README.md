# License plate and face anonymiser

This repository contains a Python script for performing real-time object detection using the trained model (model.pt) and blurring faces and licence plates in a given input video. The model model.pt, which you will see below, is implemented using the Ultralytics library and pre-trained with images data from various sources. Data annotation was done using the lableImg software. More details of the software labelImg here: https://github.com/HumanSignal/labelImg.

## Prerequisites

Before running the script, ensure you have the following dependencies installed:

- Python >= 3.9 
- OpenCV (`pip install opencv-python`)
- Ultralytics library (`pip install ultralytics`)
- torch Library as YOLO uses torch tensors. latest version should do. Please look here for installing torch: https://pytorch.org/

## Usage

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/rampallishyam/License-plate-and-face-anonymiser.git
cd License-plate-and-face-anonymiser
```

### 2. Select the pre-trained model (model.pt)

As part of this library, I have trained my model which can be found as model.pt under the folder as 'model/model.pt'. 

### 3. Run the Script

Execute the script by providing the required command-line arguments:

```bash
python videos_blurring.py --model_yolo model/model.pt --source_video_path videos/2.mp4 --output_video_path output_videos/blurred_video2.mp4
```

There are other python scripts that have the name videos_stream.py which is solely meant for selecting a video on your laptop and check how model.pt fairs on your video before performing the blurring task.

### 4. Example Output

The script will process each frame of the input video, perform object detection using YOLOv8n, and blur the detected objects. The resulting video will be saved at the specified `output_video_path`. You can adjust the blur intensity by modifying the kernel size in the `cv2.GaussianBlur` function. For instance, cv2.GaussianBlur(roi, (99, 99), 0) part of the code refers to the maximum. You can try with lower values of (99,99) tuple for instance (50,50) for a blur with lighter intensity.

##### Before blurring the faces

<video src="videos/2.mp4" controls title="Title"></video>

##### After blurring the faces

<video src="output_videos/blurred_video2.mp4" controls title="Title"></video>

## Procedure

- The YOLOv8n model is responsible for detecting objects in the video frames.
- Detected objects are then blurred using a Gaussian blur.
- Adjust the script parameters and YOLO model path according to your requirements.

Feel free to experiment with different YOLO models and parameter settings to achieve the desired object detection and blurring results.

**Note:** Ensure you have the necessary permissions to read/write files in the specified directories.

Enjoy experimenting with object detection and video processing!
