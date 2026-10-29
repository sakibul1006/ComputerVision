# Real-Time Lane Detection

Lane detection on road video using classical computer vision with OpenCV. The pipeline finds lane markings frame by frame and overlays them on the original video.

## Demo
- **Input:** frames extracted from a video of a car travelling on the Mumbai Sea Link
- **Output:** `out (1).avi`, the same video with detected lane lines drawn in colour

## Pipeline
| Step | Technique | Purpose |
|------|-----------|---------|
| 1 | Grayscale conversion | Reduce each frame to one channel |
| 2 | Gaussian blur (5×5) | Suppress noise |
| 3 | Region-of-interest mask | Keep only the road area ahead of the car |
| 4 | Binary thresholding (80) | Isolate bright lane markings |
| 5 | Canny edge detection (50, 150) | Extract edges |
| 6 | Probabilistic Hough transform | Detect line segments |
| 7 | Line overlay + video writer | Draw lanes on frames and export the video (30 fps) |

## Tech Stack
Python · OpenCV · NumPy · Matplotlib · Jupyter / Google Colab

## Repository Structure
```
ComputerVision/
├── Lane_Detection project.ipynb   # Full pipeline, step by step
├── out (1).avi                    # Output video with detected lanes
└── README.md
```

## Getting Started
1. Clone the repository
   ```bash
   git clone https://github.com/sakibul1006/ComputerVision.git
   cd ComputerVision
   ```
2. Install dependencies
   ```bash
   pip install opencv-python numpy matplotlib
   ```
3. Prepare the input: place the extracted video frames (PNG) in a folder and set the `path` variable in the notebook to that folder. The notebook was written for Google Colab, so Drive mounting cells can be skipped when running locally.
4. Run `Lane_Detection project.ipynb` from top to bottom. The output video is written as an `.avi` file.

## Limitations
- The region of interest and thresholds are tuned for this specific video.
- Curved lanes, shadows and worn markings are not handled (no perspective transform or curve fitting).

## Possible Improvements
- Read video directly with `cv2.VideoCapture` instead of extracted frames
- Average and extrapolate line segments into a single left and right lane
- Add perspective transform and polynomial lane fitting

## Author
**Sakibul SK**
[GitHub](https://github.com/sakibul1006) · [LinkedIn](https://linkedin.com/in/sakibul-sk)
