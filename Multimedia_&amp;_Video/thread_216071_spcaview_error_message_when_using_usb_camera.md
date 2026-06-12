---
title: "spcaview error message when using usb camera"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by bj00d on 2006-07-14
I have a ez cam II usb camera. When I run spcaview to test the camera, I get the following error:

:~# spcaview -d /dev/video0 -f yuv
 Spcaview version: 1.1.4 date: 27:11:2005 (C) [email]mxhaard@magic.fr[/email]
Initializing SDL.
SDL initialized.
bpp 3 format 15
Using video device /dev/video0.
Initializing v4l.
**************** PROBING CAMERA *********************
Camera found: ICM532 cam
Bridge found: TV8532
Bridge find TV8532 number 15
StreamId: GBRG Camera
Bridge find TV8532 number 15
Available Resolutions width 640  heigth 480 native
Available Resolutions width 352  heigth 288 native
Available Resolutions width 320  heigth 240 native *
Available Resolutions width 176  heigth 144 native
Available Resolutions width 160  heigth 120 native
*****************************************************
 grabbing method default MMAP asked
VIDIOCGMBUF size 2457616  frames 2  offets[0]=0 offsets[1]=1228808
VIDIOCGPICT
brightnes=32768 hue=0 color=0 contrast=32768 whiteness=0
depth=12 palette=4
VIDIOCSPICT
brightness=32768 hue=0 color=0 contrast=32768 whiteness=0
depth=24 palette=15
Couldn't set 320*240x24 video mode: No video mode large enough for 320x240

Any ideas?

---

