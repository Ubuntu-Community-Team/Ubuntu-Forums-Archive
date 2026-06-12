---
title: "webcam doesn't work but sometimes does"
date: 2010-01-16
forum: Multimedia Software
---

### Post by flyingsolo on 2010-01-16
I have a Logitech webcam (don't know the precise model name--it's a black ball shape with blue light at top) which occassionally will work with Hardy but most times does not.  I do see it is recognized when I do lsusb but if I try it with cheese, the screen is blank except for what looks like a TV test pattern of coloured bars and if I try Motion, it says the following:
```
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.9 Started
[0] ffmpeg LIBAVCODEC_BUILD 3352064 LIBAVFORMAT_BUILD 3344896
[0] Thread 1 is from /etc/motion/motion.conf
[1] Thread 1 started
[1] Failed to open video device /dev/video0: Device or resource busy
[1] Capture error calling vid_start
[1] Thread finishing...

```
I don't know why it would say /dev/video0 is busy b/c nothing is using the camera.  It does appear to be 'on' insofar as its blue light is lit.  Skype also says no video device detected.
Any suggestions?

---

