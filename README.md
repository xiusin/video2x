# Video2X Lossless Video Enlarger

### Official Discussion Group (Telegram): https://t.me/video2x

### Prerequisites

Component names that are **bolded** is mandatory.

Component names that are *italicized* can be automatically downloaded and configured with the `video2x_setup.py` script.

1. Operating System: Windows
1. AMD GPU / Nvidia GPU
1. AMD GPU driver / Nvidia GPU driver / Nvidia CUDNN
1. ***FFMPEG***
1. ***waifu2x_caffe*** / **waifu2x_converter_cpp**

## 2.4.0 (February 8, 2019)

- **Added AMD Support**. You can now use `-d/--driver waifu2x_converter` to specify the waifu2x driver to be `waifu2x_converter_cpp`. Note that you'll have to download and configure [waifu2x_converter_cpp](https://github.com/DeadSix27/waifu2x-converter-cpp/releases) first.

## 2.3.0 (February 8, 2019)

- Added the ability to specify the cache directories as required by @AusNaminator
- Fixed the problem where if there's insufficient RAM, the warning doesn't pause the script and prompt the user to reduce the amount of threads used.
- Some other minor adjustments.

## 2.2.1 (February 1, 2019)

- Fixed AAC codec error discovered by @meguerreroa

## Description

Video2X is an automation software based on waifu2x image enlarging engine. It extracts frames from a video, enlarge it by a number of times without losing any details or quality, keeping lines smooth and edges sharp.

For short: **Video2X enlarges your video without losing details**

Watch for the sharper edges in this screenshot around the shadows:

![preview](https://user-images.githubusercontent.com/21986859/49412428-65083280-f73a-11e8-8237-bb34158a545e.png)

**Or you can watch the YouTube video Demo: https://www.youtube.com/watch?v=PG94iPoeoZk**

## Screenshot
![screenshot](https://user-images.githubusercontent.com/21986859/40265170-39c0caae-5b01-11e8-8371-8b6c24769639.png)

</br>

## Installation

### Prerequisites

- **Python 3**  
Download: https://www.python.org/downloads/windows/
- **FFMPEG Windows Build**  
Download: https://ffmpeg.org/download.html  
- **waifu2x-caffe for Windows**  
Download: https://github.com/lltcggie/waifu2x-caffe/releases

### Install Dependencies

First, clone the video2x repository.

```bash
$ git clone https://github.com/K4YT3X/video2x.git
$ cd video2x/bin
```

Then you may run the `video2x_setup.py` script to install and configure the depencies automatically. This script is designed and tested on Windows 10.

This script will install `ffmpeg`, `waifu2x-caffe` to `%LOCALAPPDATA%\\video2x` and all python libraries.

```bash
$ python bin/video2x_setup.py
```

Alternatively, you can also install the dependencies manually. Please refer to the prerequisites section to see what's needed.

Then you'll need to install python dependencies before start using video2x. Install simply by executing the following command.

```bash
$ pip install -r requirements.txt
```

## Quick Start

### Nvidia CUDA (waifu2x_caffe)

Enlarge the video to 1920x1080 using CUDA. You may also use the `-r/--ratio` option.

```bash
$ python video2x.py -i video.mp4 -o video_output.mp4 -m gpu --width=1920 --height=1080
```

### Nvidia CNDNN

Enlarge the video to 1920x1080 using CUDNN. You may also use the `-r/--ratio` option.

```bash
$ python video2x.py -i video.mp4 -o video_output.mp4 -m cudnn --width=1920 --height=1080
```

### AMD or Nvidia (waifu2x_converter_cpp OpenCL)

Enlarge the video by 2 times using OpenCL. Note that `waifu2x_converter_cpp` doesn't support width and height.

```bash
$ python video2x.py -i video.mp4 -o video_output.mp4 -m gpu -r 2
```

### CPU

Enlarge the video to 1920x1080 using the CPU. You may also use the `-r/--ratio` option. This is potentially much slower than using a GPU.

```bash
$ python video2x.py -i video.mp4 -o video_output.mp4 -m cpu --width=1920 --height=1080
```


## Full Usage

```
usage: video2x.py [-h] -i INPUT -o OUTPUT -m {cpu,gpu,cudnn} -d
                  {waifu2x_caffe,waifu2x_converter}
                  [-y {upconv_7_anime_style_art_rgb,upconv_7_photo,anime_style_art_rgb,photo,anime_style_art_y}]
                  [-t THREADS] [-c CONFIG] [--width WIDTH] [--height HEIGHT]
                  [-r RATIO]

optional arguments:
  -h, --help            show this help message and exit

Basic Options:
  -i INPUT, --input INPUT
                        Specify source video file/directory
  -o OUTPUT, --output OUTPUT
                        Specify output video file/directory
  -m {cpu,gpu,cudnn}, --method {cpu,gpu,cudnn}
                        Specify upscaling method
  -d {waifu2x_caffe,waifu2x_converter}, --driver {waifu2x_caffe,waifu2x_converter}
                        Waifu2x driver
  -y {upconv_7_anime_style_art_rgb,upconv_7_photo,anime_style_art_rgb,photo,anime_style_art_y}, --model_type {upconv_7_anime_style_art_rgb,upconv_7_photo,anime_style_art_rgb,photo,anime_style_art_y}
                        Specify model to use
  -t THREADS, --threads THREADS
                        Specify number of threads to use for upscaling
  -c CONFIG, --config CONFIG
                        Manually specify config file

Scaling Options:
  --width WIDTH         Output video width
  --height HEIGHT       Output video height
  -r RATIO, --ratio RATIO
                        Scaling ratio
```

This project is based on the following softwares and projects.
- [FFMPEG]('https://www.ffmpeg.org/')
- [waifu2x caffe](https://github.com/lltcggie/waifu2x-caffe)
- [waifu2x-converter-cpp](https://github.com/DeadSix27/waifu2x-converter-cpp)