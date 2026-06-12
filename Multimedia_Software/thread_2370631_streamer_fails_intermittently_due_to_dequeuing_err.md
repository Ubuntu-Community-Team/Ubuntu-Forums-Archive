---
title: "streamer fails intermittently due to dequeuing error"
date: 2017-09-05
forum: Multimedia Software
---

### Post by redpanda86 on 2017-09-05
I'm running an [AV.io video capture device]("https://www.epiphan.com/products/avio-hd/") into an Nvidia Jetson TX1 / Ubuntu 14.04 by USB. Video is being captured constantly in 1-minute segments, controlled by a python script - the script includes a loop which executes

```
streamer -f jpeg -r 24 -t 00:01:00 -s 1024x768 -o /media/<myName>/<mounted_hard_drive>/video/<timestamp>.avi
```


The streamer command is blocking - after completion, the loop restarts to collect a new file.


I'm finding that this loop will run fine for some number of times and then hang. If I end the script after a hang and try executing the command myself, it produces


    ```
avi / video: JPEG (JFIF) / audio: nonelibv4l2: error turning on stream: Input/output error
ioctl: VIDIOC_STREAMON(int=1): Input/output error
libv4l2: error dequeuing buf: Invalid argument
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x1 [MAPPED];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Invalid argument
libv4l2: error dequeuing buf: Invalid argument
ioctl: VIDIOC_DQBUF(index=0;type=VIDEO_CAPTURE;bytesused=0;flags=0x1 [MAPPED];field=ANY;;timecode.type=0;timecode.flags=0;timecode.frames=0;timecode.seconds=0;timecode.minutes=0;timecode.hours=0;timecode.userbits="";sequence=0;memory=MMAP): Invalid argument
...
```

...which repeats indefinitely.

Checking ```
dmesg
``` yields


    ```
[349165.022455] uvcvideo: Failed to set UVC commit control : -32 (exp. 26).
[349165.030431] uvcvideo 1-3.1:1.2: resume error -5
[349165.044671] compat_ioctl32: unknown ioctl 'V', dir=3, #26 (0xc050561a)
[349165.051647] compat_ioctl32: unknown ioctl 'V', dir=3, #26 (0xc050561a)
[349165.051716] compat_ioctl32: unknown ioctl 'V', dir=3, #25 (0xc0485619)
[349165.087061] uvcvideo: Failed to set UVC commit control : -32 (exp. 26).
```


htop shows no issues with disk space or memory.


Why is streamer spontaneously failing, and how can I go about debugging this problem?


RE streamer alternatives:


I've tried doing capture with ffmpeg and gstreamer, and wasn't able to get them working whereas streamer worked out of the box.

---

