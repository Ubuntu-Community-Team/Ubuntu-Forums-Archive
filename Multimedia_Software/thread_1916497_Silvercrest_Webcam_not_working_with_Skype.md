---
title: "Silvercrest Webcam not working with Skype"
date: 2012-01-28
forum: Multimedia Software
---

### Post by hilz on 2012-01-28
I've tried reading a number of posts on similar subjects but still not able to get my webcam working with Skype.

[COLOR=Navy]$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID eb1a:2710 eMPIA Technology, Inc. SilverCrest Webcam
Bus 006 Device 002: ID 0461:4d22 Primax Electronics, Ltd 
Bus 007 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard

$ lsmod | grep v4l
v4l2_common            15793  2 mt9v011,em28xx
videodev               85626  3 mt9v011,em28xx,v4l2_common

$ luvcview
luvcview 0.2.6

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: YUYV (MJPG is not supported by device)
  Frame size:   640x480
  Frame rate:   0.005 fps (requested frame rate 30 fps is not supported by device)
Unable to map buffer: Invalid argument
 Init v4L2 failed !! exit fatal[/COLOR]

I've tried using these:
[COLOR=Navy]
$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
[/COLOR][COLOR=Navy]$ LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype[/COLOR]

[COLOR=Black]Is there anything else I can try?[/COLOR]

---

