---
title: "Low fps using motion ?"
date: 2019-09-03
forum: Multimedia Software
---

### Post by not4u on 2019-09-03
Hi All!

I am trying to use motion to create a video stream with 30fps and 640x480, but getting low (10-11 fps) framerate even though the camera ( /dev/video0 ) seems to support the 30. The CPU is a Raspberry 4 4GB version, but I experience the same issue on an i5 8GB PC as well.

**v4l2-ctl --list-formats-ext says:**
> ioctl: VIDIOC_ENUM_FMT
        Type: Video Capture


        [0]: 'MJPG' (Motion-JPEG, compressed)
                Size: Discrete 640x480
                        Interval: Discrete 0.033s (30.000 fps)
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 320x240
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 800x600
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 1024x768
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 1280x720
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 1280x1024
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 1600x1200
                        Interval: Discrete 0.067s (15.000 fps)
                Size: Discrete 1920x1080
                        Interval: Discrete 0.067s (15.000 fps)
                Size: Discrete 2048x1536
                        Interval: Discrete 0.067s (15.000 fps)
                Size: Discrete 2592x1944
                        Interval: Discrete 0.067s (15.000 fps)
                Size: Discrete 640x480
                        Interval: Discrete 0.033s (30.000 fps)
                        Interval: Discrete 0.033s (30.000 fps)
        [1]: 'YUYV' (YUYV 4:2:2)
                Size: Discrete 640x480
                        Interval: Discrete 0.033s (30.000 fps)
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 320x240
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 800x600
                        Interval: Discrete 0.033s (30.000 fps)
                Size: Discrete 1024x768
                        Interval: Discrete 0.067s (15.000 fps)
                Size: Discrete 1280x720
                        Interval: Discrete 0.133s (7.500 fps)
                Size: Discrete 1280x1024
                        Interval: Discrete 0.133s (7.500 fps)
                Size: Discrete 1600x1200
                        Interval: Discrete 0.333s (3.000 fps)
                Size: Discrete 1920x1080
                        Interval: Discrete 0.333s (3.000 fps)
                Size: Discrete 2048x1536
                        Interval: Discrete 0.333s (3.000 fps)
                Size: Discrete 2592x1944
                        Interval: Discrete 0.333s (3.000 fps)
                Size: Discrete 640x480
                        Interval: Discrete 0.033s (30.000 fps)
                        Interval: Discrete 0.033s (30.000 fps)




**Motion conf:**
> videodevice /dev/video0
stream_quality 100
stream_maxrate 30
stream_port 8080
stream_localhost off
output_pictures off
framerate 30
v4l2_palette 8
[http://127.0.0.1:8080/1.cgi](http://127.0.0.1:8080/1.cgi)
width 640
height 480
auto_brightness off
contrast 0
saturation 0
text_left Changed pixels: %D\nFrame num: %q

Can someone help me out on how to set motion to get the 30fps?

THanks!

---

