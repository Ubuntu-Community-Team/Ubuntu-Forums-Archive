---
title: "Need a v4l2 wiz: dqbuf failure"
date: 2009-12-27
forum: Multimedia Software
---

### Post by AR_Kozz on 2009-12-27
I installed gspca-ov534 recently to get my ps eye working. Compiled and installed well under: 2.6.24.x, 2.6.27-16 intrepid, then jaunty, now under kernel 2.6.29.6. Camera detects fine by all apps, including video attributes.

The fail is the demux. vlc reports "failure to wait" blamed on VIDIOC_DQBUF (in v4l2-ioctl.c)

same happens with both mmap and read methods. Other apps (mplayer, xawtv, etc) generally report "select timeout." 

Here's mainly what happens in the vlc log file: 

```
main debug: starting new item
main debug: processing request item null node Playlist skip 0
main debug: creating new input thread
main debug: Creating an input for 'v4l2:///dev/video0'
main debug: thread started
main debug: waiting for thread initialization
main debug: `v4l2:///dev/vidmeo0' gives access `v4l2' demux `' path `/dev/video0'
main debug: creating demux: access='v4l2' demux='' path='/dev/video0'
main debug: looking for access_demux module: 1 candidate
v4l2 debug: ALSA input support available
v4l2 debug: Trying direct kernel v4l2
v4l2 debug: main device='/dev/video0'
v4l2 debug: trying device '/dev/video0' as video
v4l2 debug: V4L2 device: USB Camera-B4.04.27.1 using driver: ov534 (version: 2.5.0) on usb-0000:00:1f.4-1
v4l2 debug: the device has the capabilities: (X) Video Capure, ( ) Audio, ( ) Tuner
v4l2 debug: supported I/O methods are: (X) Read/Write, (X) Streaming, ( ) Asynchronous
v4l2 debug: video input 0 (ov534) has type: External analog input *
v4l2 debug: device supports chroma YUY2 [YUYV, YUYV]
v4l2 warning: Unable to query for frame sizes
v4l2 debug: device supports chroma YUYV [YUYV, YUYV]
v4l2 warning: Unable to query for frame sizes
v4l2 debug: '/dev/video0' is a video device
v4l2 debug: Extended control API supported by v4l2 driver
v4l2 debug: Available control: Red Balance (98090e)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 255 by steps of 1
v4l2 debug:     default value: 128
v4l2 debug:     current value: 128
v4l2 debug: Available control: Blue Balance (98090f)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 255 by steps of 1
v4l2 debug:     default value: 128
v4l2 debug:     current value: 128
v4l2 debug: Available control: Exposure (980911)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 255 by steps of 1
v4l2 debug:     default value: 255
v4l2 debug:     current value: 255
v4l2 debug: Available control: Autogain (980912)
v4l2 debug:     boolean control
v4l2 debug:     default value: 1
v4l2 debug:     current value: 1
v4l2 debug: Available control: Main Gain (980913)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 63 by steps of 1
v4l2 debug:     default value: 20
v4l2 debug:     current value: 20
v4l2 debug: Available control: HFlip (980914)
v4l2 debug:     boolean control
v4l2 debug:     default value: 0
v4l2 debug:     current value: 0
v4l2 debug: Available control: VFlip (980915)
v4l2 debug:     boolean control
v4l2 debug:     default value: 0
v4l2 debug:     current value: 0
v4l2 debug: Available control: Sharpness (98091b)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 63 by steps of 1
v4l2 debug:     default value: 0
v4l2 debug:     current value: 4
v4l2 error: device does not support mmap i/o
v4l2 debug: Trying libv4l2 wrapper
v4l2 debug: opening '/dev/video0' as video
v4l2 debug: V4L2 device: USB Camera-B4.04.27.1 using driver: ov534 (version: 2.5.0) on usb-0000:00:1f.4-1
v4l2 debug: the device has the capabilities: (X) Video Capure, ( ) Audio, ( ) Tuner
v4l2 debug: supported I/O methods are: (X) Read/Write, (X) Streaming, ( ) Asynchronous
v4l2 debug: video input 0 (ov534) has type: External analog input *
v4l2 error: cannot get video input characteristics (Invalid argument)
v4l2 debug: opening '(null)' as audio
main debug: thread 2966473616 (input) created at priority 10 (input/input.c:370)
v4l2 error: cannot open device hw for ALSA audio (Device or resource busy)
v4l2 error: cannot open device /dev/dsp for OSS audio (Device or resource busy)
main warning: no access_demux module matching "v4l2" could be loaded
main debug: TIMER module_Need() : 239.872 ms - Total 239.872 ms / 1 intvls (Avg 239.872 ms)
main debug: creating access 'v4l2' path='/dev/video0'
main debug: looking for access module: 1 candidate
v4l2 debug: Trying direct kernel v4l2
v4l2 debug: main device='/dev/video0'
v4l2 debug: trying device '/dev/video0' as video
v4l2 debug: V4L2 device: USB Camera-B4.04.27.1 using driver: ov534 (version: 2.5.0) on usb-0000:00:1f.4-1
v4l2 debug: the device has the capabilities: (X) Video Capure, ( ) Audio, ( ) Tuner
v4l2 debug: supported I/O methods are: (X) Read/Write, (X) Streaming, ( ) Asynchronous
v4l2 debug: video input 0 (ov534) has type: External analog input *
v4l2 debug: device supports chroma YUY2 [YUYV, YUYV]
v4l2 warning: Unable to query for frame sizes
v4l2 debug: device supports chroma YUYV [YUYV, YUYV]
v4l2 warning: Unable to query for frame sizes
v4l2 debug: '/dev/video0' is a video device
v4l2 debug: Extended control API supported by v4l2 driver
v4l2 debug: Available control: Red Balance (98090e)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 255 by steps of 1
v4l2 debug:     default value: 128
v4l2 debug:     current value: 128
v4l2 debug: Available control: Blue Balance (98090f)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 255 by steps of 1
v4l2 debug:     default value: 128
v4l2 debug:     current value: 128
v4l2 debug: Available control: Exposure (980911)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 255 by steps of 1
v4l2 debug:     default value: 255
v4l2 debug:     current value: 255
v4l2 debug: Available control: Autogain (980912)
v4l2 debug:     boolean control
v4l2 debug:     default value: 1
v4l2 debug:     current value: 1
v4l2 debug: Available control: Main Gain (980913)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 63 by steps of 1
v4l2 debug:     default value: 20
v4l2 debug:     current value: 20
v4l2 debug: Available control: HFlip (980914)
v4l2 debug:     boolean control
v4l2 debug:     default value: 0
v4l2 debug:     current value: 0
v4l2 debug: Available control: VFlip (980915)
v4l2 debug:     boolean control
v4l2 debug:     default value: 0
v4l2 debug:     current value: 0
v4l2 debug: Available control: Sharpness (98091b)
v4l2 debug:     integer control
v4l2 debug:     valid values: 0 to 63 by steps of 1
v4l2 debug:     default value: 0
v4l2 debug:     current value: 4
v4l2 debug: opening '(null)' as audio
v4l2 error: cannot open device hw for ALSA audio (Device or resource busy)
v4l2 error: cannot open device /dev/dsp for OSS audio (Device or resource busy)
main debug: using access module "v4l2"
main debug: TIMER module_Need() : 44.638 ms - Total 44.638 ms / 1 intvls (Avg 44.638 ms)
main debug: Using AStream*Stream
main debug: pre-buffering...
qt4 debug: Error while initializing qt-specific localization
qt4 debug: Updating the stream status: 3
main debug: incoming request - stopping current input
main debug: dying input
main debug: dying input
main debug: dying input
main debug: dying input
main debug: dying input
main debug: dying input
main debug: dying input
main error: cannot pre fill buffer
main warning: cannot create a stream_t from access
main debug: removing module "v4l2"
main debug: thread ended
qt4 debug: Updating the stream status: 8
main debug: dead input
main debug: thread 2966473616 joined (playlist/engine.c:244)
main debug: TIMER input launching for 'v4l2:///dev/video0' : 50426.622 ms - Total 50426.622 ms / 1 intvls (Avg 50426.620 ms)
```

same thing happens when libv4l2 is forced.

VLC lays the blame on VIDIOC_DQBUF in the terminal. How do I debug v4l2 to make it dequeue the buffer like it should

(could be hardware but I doubt it. My pc is old but has a video card and plays just about everything well)

---

