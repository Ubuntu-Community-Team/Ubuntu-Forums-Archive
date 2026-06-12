---
title: "xawtv errors out when trying to record video"
date: 2011-10-20
forum: Multimedia Software
---

### Post by xdunlapx on 2011-10-20
I'm trying to use xawtv to record video with audio. I keep getting an error when recording video and the video never records properly. The error is "error [init]"

I chose the avi driver and typed in /home/brittany/test.avi for the file name and left everything else as it was. My webcam is showing up properly in the preview window. Any help getting this to work will be greatly appreciated. Thank you.

---

### Post by no2498 on 2011-10-21
install guvcview
see if it works better
or try this in a terminal
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so xawtv

---

### Post by xdunlapx on 2011-10-21
> **no2498 said:**
> install guvcview
see if it works better
or try this in a terminal
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so xawtv

guvcview crashes when I try to capture an image or video.

xawtv still has error [init]

I did see that when running xawtv with the above command that /dev/video0 [v4l2]: no overlay support 


```
brittany@kubuntu:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so xawtv
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
This is xawtv-3.95.dfsg.1, running on Linux/x86_64 (3.0.0-12-generic)
xinerama 0: 1600x900+0+0
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
WARNING: No DGA direct video mode for this display.
/dev/video0 [v4l2]: no overlay support
v4l-conf had some trouble, trying to continue anyway
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct
ioctl: VIDIOC_G_STD(std=0x2786090 [PAL_I,PAL_K,NTSC_M_JP,?,SECAM_H,SECAM_K,SECAM_K1,SECAM_L,(null)]): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963778;value=64): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963776;value=0): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963779;value=0): Invalid argument
ioctl: VIDIOC_S_CTRL(id=9963777;value=0): Invalid argument
ioctl: VIDIOC_S_STD(std=0x0 []): Invalid argument
oss: open /dev/dsp: No such file or directory

```

---

### Post by no2498 on 2011-10-22
its been to long to remember how to make the preload into a bin/bash file
you only need to make one file
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype



#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype
if you are using 64 bit you may need to install the 32 bit lib's

---

### Post by xdunlapx on 2011-10-22
> **no2498 said:**
> its been to long to remember how to make the preload into a bin/bash file
you only need to make one file
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype



#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype
if you are using 64 bit you may need to install the 32 bit lib's

skype? Does skype record video? I tried that command with xawtv and it didn't work. Gave errors.

---

### Post by no2498 on 2011-10-23
thats odd guvcview and xawtv seem to be the first i can get working
give wxcam a try
you can get it in a deb file also
[http://sourceforge.net/projects/wxcam/?_test=beta](http://sourceforge.net/projects/wxcam/?_test=beta)
it may also be in your repose

---

