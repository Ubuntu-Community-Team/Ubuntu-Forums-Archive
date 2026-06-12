---
title: "How to detect frame size from IPEVO doc camera."
date: 2015-05-06
forum: Multimedia Software
---

### Post by wgw on 2015-05-06
I have a IPEVO Ziggy doc camera ([http://www.ipevo.com/prods/IPEVO-Ziggi-HD-USB-Document-Camera](http://www.ipevo.com/prods/IPEVO-Ziggi-HD-USB-Document-Camera)). Linux not supported!, but it sort of works. The only problem is that it is dropping frames. Here is the mplayer output. Any suggestions for how to fix this? I am dangerously close to getting it to work. 

```
bill@bill-laptop:~$ mplayer tv:// -tv driver=v4l2:width=640:height=480:device=/dev/video0
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
v4l2: your device driver does not support VIDIOC_G_STD ioctl, VIDIOC_G_PARM was used instead.
Selected device: IPEVO VZ-1 HD
 Capabilities:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Inappropriate ioctl for device
Error: Cannot set norm!
Selected input hasn't got a tuner!
v4l2: ioctl set mute failed: Invalid argument
Failed to open VDPAU backend libvdpau_r300.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
====================================
Opening video decoder: [raw] RAW Uncompressed Video
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 640x480 => 640x480 Packed YUY2 
Selected video codec: [rawyuy2] vfm: raw (RAW YUY2)
===================================
Audio: no sound
Starting playback...
V:   0.0   1/  1 ??% ??% ??,?% 0 0 
Frame too small! (2826<614400) Wrong format?
V:   0.0   4/  4 ??% ??% ??,?% 0 0 
Frame too small! (1867<614400) Wrong format?
V:   0.0  15/ 15 ??% ??% ??,?% 0 0 
Frame too small! (2065<614400) Wrong format?
V:   0.0  19/ 19 ??% ??% ??,?% 0 0 
Frame too small! (2312<614400) Wrong format?
V:   0.0  23/ 23 ??% ??% ??,?% 0 0 
Frame too small! (1888<614400) Wrong format?
V:   0.0  32/ 32 ??% ??% ??,?% 0 0 
Frame too small! (1881<614400) Wrong format?
V:   0.0  38/ 38 ??% ??% ??,?% 0 0 
Frame too small! (2410<614400) Wrong format?
V:   0.0  47/ 47 ??% ??% ??,?% 0 0 
Frame too small! (104428<614400) Wrong format?
V:   0.0  54/ 54 ??% ??% ??,?% 0 0 
v4l2: ioctl set mute failed: Invalid argument
v4l2: 56 frames successfully processed, 446 frames dropped.

```

---

