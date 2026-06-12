---
title: "Problem using creative webcam"
date: 2010-01-07
forum: Multimedia Software
---

### Post by rustyshakelford2 on 2010-01-07
I have a creative pc cam 300 that i have been trying to set up as a security camera, on a computer running ubuntu 9.10. I tried installing the spca5xx driver, but i can only find it for old versions of ubuntu and it doesnt work. Does anyone know how to get the driver working?

---

### Post by no2498 on 2010-01-08
do you have a program to see the cam with
like (cheese) or this 1 i like (wxcam) im on 804 and use wxcam 1.0.2
open a terminal type (gstreamer-properties) click enter
click video try v4l1 or v4l2 
just to see if it comes on

---

### Post by rustyshakelford2 on 2010-01-26
> **no2498 said:**
> do you have a program to see the cam with
like (cheese) or this 1 i like (wxcam) im on 804 and use wxcam 1.0.2
open a terminal type (gstreamer-properties) click enter
click video try v4l1 or v4l2 
just to see if it comes on

I get an error that says "Cannot identify device /dev/video0"
I also tried installing easycam, it identified my webcam and installed a driver, but cheese still says there was no webcam detected. Is there maby a way to have virtualbox connect to the device so i can just use the windows driver? it doesnt show up in the list of usb devices.

---

### Post by no2498 on 2010-01-27
ok do this
open a terminal type (gstreamer-properties) click enter
click video try v4l1 or v4l2
click the bottom test for each 1

cheese has a nice help

---

