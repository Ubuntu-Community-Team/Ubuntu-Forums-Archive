---
title: "PB-tv200 usb tv (WIS Technologies, Inc. WinFast WalkieTV TV Load)"
date: 2010-12-14
forum: Multimedia Software
---

### Post by stkontra on 2010-12-14
Hi everyone,

I have a PB-tv200  analog USB TV receiver. There is an s-video composite input on it that I would like to use. It works fine on windows but no luck under linux. 

istvan@istvan ~ $ lsusb
Bus 002 Device 006: ID 19d2:0001 ONDA Communication S.p.A. 
Bus 002 Device 004: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 010: ID 0eb1:6666 WIS Technologies, Inc. WinFast WalkieTV TV Loader
Bus 001 Device 008: ID 0930:0b09 Toshiba Corp. PX1396E-3T01 External hard drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

As you can see my computer can recognize it as 'WIS Technologies, Inc. WinFast WalkieTV TV Loader'  when it's connected.

But when I start 'tvtime', I get the following message in the terminal:

istvan@istvan ~ $ tvtime
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/istvan/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video1: No such file or directory
mixer: Can't open device /dev/mixer, mixer volume and mute unavailable.
Segmentation fault

Probably I will need to install some firmware but I don't know what.

When I run the gstreamer-properties

istvan@istvan ~ $ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(488): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: No such file or directory]

it doesen't show in the multimedia selector.

If you have any idea how I could get it worked, I would really appreciate it.

Thanks in advance.

---

