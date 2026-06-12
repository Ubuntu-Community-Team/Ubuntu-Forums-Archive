---
title: "Trouble using Logitech Quickcam Easy/Cool with Skype"
date: 2011-04-13
forum: Multimedia Software
---

### Post by uselessuser on 2011-04-13
an't get my webcam to work... with anything, letalone skype. lsusb  feedback Bus 002 Device 002: ID 046d:08af Logitech, Inc. QuickCam  Easy/Cool

and also, when i use dmesg | less part of the feedback i get is:
 34.574085]  /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c:  USB GSPCA camera found.(ZC3XX) 
[   35.183847] usbcore: registered new interface driver gspca
[   35.183855]  /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c:  gspca driver 01.00.20 registered

i'm pretty sure i have the right drivers there, the system seems to know  there's a camera there, i just can't figure out how to make the camera  work with any of the softare i need it for. it isn't detected in Skype  Static, so I tried using it with ekiga and i got : Error while opening  video device /dev/.static/dev/video0

i really need to get this camera working, or find another one that'll  work outta the box... oh, and before anyone asks, i'm using  v.2.6.24-29-generic - xubuntu

help? i'm totally lost... i've been teaching myself a lot about linux  lately, and haven't had to ask for help until now, but i'm totally lost,  and totally noob. i'ma chef by trade, so if you explain something to  me... it has to be VERY laymans terms please

---

### Post by no2498 on 2011-04-13
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

