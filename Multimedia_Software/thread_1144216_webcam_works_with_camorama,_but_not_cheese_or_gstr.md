---
title: "webcam works with camorama, but not cheese or gstreamer-properties"
date: 2009-04-30
forum: Multimedia Software
---

### Post by 01000111 on 2009-04-30
My Logitech Quickcam Web works perfectly with Camorama.  It also works when I run VirtualBox with WinXP, but it doesn't work when I test with gstreamer-properties or Cheese.  I'm really trying to get it to work on the mebeam.com website, but Adobe Flash doesn't find the camera and I thought if I can get Cheese working, that might fix the Flash issue.

I have to use the 'qcset compatible=dblbuf' command to get camorama to work.

Any assistance is appreciated.

01000111
Xubuntu 9.04 AMD64




lsusb:
Bus 002 Device 003: ID 046d:0850 Logitech, Inc. QuickCam Web


dmesg:
[    8.612596] quickcam: QuickCam USB camera found (driver version QuickCam USB 0.6.6 $Date: 2006/11/04 08:38:14 $)
[    8.612602] quickcam: Kernel:2.6.28-11-generic bus:2 class:FF subclass:FF vendor:046D product:0850
[    8.656042] quickcam: Sensor VV6410 detected
[    8.662174] quickcam: Registered device: /dev/video0
[    8.662218] usbcore: registered new interface driver quickcam


gstreamer-properties:
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(198): gst_v4l_open (): /GstPipeline:pipeline0/GstV4lSrc:v4lsrc3:
Device opened, but wrong type (0x0)]

---

### Post by maheshasolkar on 2009-08-14
Same here. Haven't been able to find anything on the web *yet* that helps.

---

