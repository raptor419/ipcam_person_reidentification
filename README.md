<!-- TOC -->

- [Person Re-identification](#person-re-identification)
    - [What's this](#whats-this)
    - [Tested Environment](#tested-environment)
    - [Required Python packages](#required-python-packages)
    - [Other Requirements](#reference)
        - [OpenVINO Toolkit and Flask Video streaming](#openvino-toolkit-and-flask-video-streaming)
        - [OpenVINO Intel Model](#openvino-intel-model)
    - [How to use](#how-to-use)
    - [Run app](#run-app)

<!-- /TOC -->

# Person Re-identification over IP Camera Network

## What's this

This is Person Identification Test App using Person Re-Identification Models.

You can do followings:

* Person Detection
* Preson Re-Identification (Tracking and Counter)


## Tested Environment

- Python 3.7.6
- Windows 10
- OpenVINO Toolkit Latest


## Required Python packages

```sh
pip install -r requirements.txt
```

## Other Requirements

### OpenVINO Toolkit
* [Install OpenVINO Toolkit](https://docs.openvinotoolkit.org/latest/index.html)

###  PRID Models (Already optimized and kept in this github)

* [person-detection-retail-0013](https://github.com/openvinotoolkit/open_model_zoo/blob/master/models/intel/person-detection-retail-0013/description/person-detection-retail-0013.md)
* [person-reidentification-retail-0031](https://github.com/openvinotoolkit/open_model_zoo/blob/2020.3/models/intel/person-reidentification-retail-0031/description/person-reidentification-retail-0031.md)


## How to use

```sh
python app.py -h
usage: app.py [-h] -i INPUT(filename, cam for PC camera or ipcam) [-d {CPU,GPU,FPGA}]
              [-d_reid {CPU,GPU,FPGA,MYRIAD}] [--v4l] [-ax {0,1}] [-g GRID]

optional arguments:
  -h, --help            show this help message and exit
  -i INPUT, --input INPUT
                        Path to video file or image. 'cam' for capturing video
                        stream from camera
  -d {CPU,GPU}, --device {CPU,GPU}
                        Specify the target device for Person Detection to
                        infer on; CPU, GPU, FPGA is acceptable.
  -d_reid {CPU,GPU}, --device_reidentification {CPU,GPU}
                        Specify the target device for person re-identificaiton
                        to infer on; CPU, GPU, FPGA is acceptable.
  --v4l                 cv2.VideoCapture with cv2.CAP_V4L
  -ax {0,1}, --axis {0,1}
                        Specify the axis when counting person horizontally or
                        vertically (0: count horizontally(x-axis) , 1: count
                        vertically (y-axis)
  -g GRID, --grid GRID  Specify how many grid to divide frame. This is used to
                        define boundary area when the tracker counts person. 0
                        ~ 2 means not counting person. (range: 3 < max_grid)

```


## Run app

**example1.** camera streaming without person counter 

```sh
python app.py -i ipcam
```

**example2** Specify video file with person counter

```py
python app.py -i P1033674_1920.mp4 --grid 10 
```


Access the url bellow on your browser

```txt
http://127.0.0.1:5000/
```
