---
title: "&lt;B&gt;How to install webcam?&lt;/B&gt;"
date: 2010-05-06
forum: Multimedia Software
---

### Post by wired99 on 2010-05-06
How do I install a webcam?

I have an usb Logitech Quickcam

The program Cheese looks for a camera in "/dev/video0" but it is greyed-out

"lsusb" shows the following:
Bus 002 Device 005: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 003: ID 046d:08f6 Logitech, Inc. QuickCam Messenger Plus
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

How do I install the webcam so that it is recognized by programs?

I'm using Ubuntu 10.04
Gnome 2.30.0

---

### Post by no2498 on 2010-05-07
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

try the cam in cheese

if it does not come on try this

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

---

### Post by wired99 on 2010-05-07
This is the result I get:

me@buntu:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese
libv4l2: error turning on stream: Input/output error


These are my results from gstreamer-properties

v4l:
me@buntu:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux (v4l)': Could not get/set settings from/on resource. [v4l_calls.c(4188): gst_v4l_set_chan_norm (): /GstPipeline:ppipeline0/GstV4lSrc:v4lsrc1:
Error setting the channel/norm settings: Invalid argument]

v4l2 (device:default and also device:camera)
me@buntu:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
libv4l2: error turning on stream: Input/output error
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1952): gst_v4l2_object_start_streaming (): /GstPipeline:ppipeline0/GstV4l2Src:v4l2src1:
system error: Input/output error]


any suggestions?

---

### Post by afrodeity on 2010-07-04
Wondering if the plugins are installed in the kernel or not? I also have similar problem with Skype.

---

