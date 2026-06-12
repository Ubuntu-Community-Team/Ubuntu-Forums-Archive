---
title: "Logitech Quickcam 3500 E not working"
date: 2011-08-23
forum: Multimedia Software
---

### Post by bouncy35 on 2011-08-23
Hi,

I have 11.04 installed and am trying to use a Logitech Quickcam 3500E on an Asus 5431 laptop but I cannot get video to be displayed. I have got the microphone working and I can control the LED on the top of the camera using gstreamer-properties.

dmesg gives: uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a4)

According to the Ubuntu pages this is the correct id number for the camera and it is apparently supported fully by the uvc driver.

Video does not appear in gstreamer-properties test button, nor cheese, nor skype nor empathy

I have Medibuntu repositories installed

The camera works fine on Windows and Mac and used to work on a Samsung N10 netbook with 11.04

However the in-built webcam on the laptop works fine so I am thinking that there may be a hardware conflict.

I think I must have read almost every google post about this issue and tried a lot of different things none of which have worked. :confused:

Any ideas anyone?

Thanks in advance.

---

### Post by no2498 on 2011-08-24
see if this helps
in a terminal type
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype click enter

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so cheese

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so empathy

if yes you need to make a /bin/bash file for it you only need to make 1

---

