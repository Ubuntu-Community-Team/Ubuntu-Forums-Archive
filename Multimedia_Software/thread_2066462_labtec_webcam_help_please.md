---
title: "labtec webcam help please"
date: 2012-10-04
forum: Multimedia Software
---

### Post by secretreeve on 2012-10-04
[IMG]http://www.labtec.com/lang/images/0/241.jpg[/IMG]

thats the webcam, cheap tacky and dull i know. but its all i got and i just need it for some youtube vids of model making.

can someone guide me through how to install it please?

lsusb shows its plugged in as a logitec corp labtec webcam pro.

but i cannot get it to output on cheese (black window) or guvcviewer (white window)

so i really need some help.

tried following one of the guides but got this in the first step

```
root@chris-desktop:~# apt-get install build-essential linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree       
Reading state information... Done
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to locate package linux-headers-uname -r

```


oh and its ubuntu 12.04 or which ever the latest release is. thanks.

---

### Post by jsantiagogo on 2013-04-19
I have a similar problem with same labtec webcam pro.
I wrote "[COLOR=#333333][FONT=Ubuntu] [/FONT][/COLOR][COLOR=#006400][FONT=Ubuntu]gstreamer-properties[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]" in a terminal. 
I got: 
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][COLOR=#006400](gstreamer-properties:5345): Gtk-WARNING **: Unknown property: GtkDialog.has-separator[/COLOR][/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][COLOR=#006400](gstreamer-properties:5345): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
libv4l2: error setting pixformat: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 640x480 [gstv4l2object.c(2197): gst_v4l2_object_set_format (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
Call to S_FMT failed for YU12 @ 640x480: Invalid argument]
libv4l2: error setting pixformat: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 640x480 [gstv4l2object.c(2197): gst_v4l2_object_set_format (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src2:
Call to S_FMT failed for YU12 @ 640x480: Invalid argument]
libv4l2: error setting pixformat: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 640x480 [gstv4l2object.c(2197): gst_v4l2_object_set_format (): /GstPipeline:pipeline6/GstV4l2Src:v4l2src3:
Call to S_FMT failed for YU12 @ 640x480: Invalid argument]
libv4l2: error setting pixformat: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Device '/dev/video0' cannot capture at 640x480 [gstv4l2object.c(2197): gst_v4l2_object_set_format (): /GstPipeline:pipeline7/GstV4l2Src:v4l2src4:
Call to S_FMT failed for YU12 @ 640x480: Invalid argument]
[/COLOR]
And when I tested, resulted: [COLOR=#006400]"Video for Linux 2 (v4l2): Device '/dev/video0' cannot capture at 640x480"[/COLOR]
My device is: [COLOR=#006400]USBCamera (046d:08a2) [/COLOR][/FONT][/COLOR]

---

