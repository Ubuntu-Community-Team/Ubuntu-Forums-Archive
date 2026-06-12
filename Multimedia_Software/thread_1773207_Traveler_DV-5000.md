---
title: "Traveler DV-5000"
date: 2011-06-01
forum: Multimedia Software
---

### Post by elcaudillostijn on 2011-06-01
I have a Traveler DV-5000 camera and it has a webcam function as well. At least that webcam function works without a problem on Windows. But I love to work with Ubuntu and Linux in general, so I find it really annoying when I have to use Skype or whatever and I need my webcam I have to switch to Windows... 
The camera has a driver for its webcam on Windows, but I'm afraid I can't find anything for Ubuntu so far. And I've read about a billion threads about webcam and etc. 
Does anyone know what to do? Or should I just switch to Windows everytime I need my cam.

---

### Post by no2498 on 2011-06-02
plug in the cam turn it on
open a terminal type dmesg click enter
after it stops type lsusb click enter
do you see the cam in the list if yes

type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

---

### Post by elcaudillostijn on 2011-06-02
stijn@stijn-linux:~$ lsusb
Bus 002 Device 007: ID 04f2:a216 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
stijn@stijn-linux:~$ gstreamer-properties
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
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Kan apparaat '/dev/video0' niet identificeren. [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src1:
system error: Bestand of map bestaat niet]

(gstreamer-properties:2277): GLib-GObject-WARNING **: invalid cast from `GtkBuilder' to `GtkWidget'

(gstreamer-properties:2277): Gtk-CRITICAL **: IA__gtk_widget_get_screen: assertion `GTK_IS_WIDGET (widget)' failed

That's what I get ... When I open Gstreamer it doesn't find anything (as I expected since I have tried this before). It's odd tho, cuz when I type lsusb it seems to detect my hardware 'Chicony Electronics' .. Since I have no idea what this is and I do know all of the others, I guess that must be my cam. 
But no luck whatsoever to get the damn thing working.
But thanks for trying to help!

---

### Post by no2498 on 2011-06-03
[http://www.google.com/search?client=opera&rls=en&q=04f2:a216+Chicony+Electronics+Co.,+Ltd&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=04f2:a216+Chicony+Electronics+Co.,+Ltd&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)

hope you can find something

---

