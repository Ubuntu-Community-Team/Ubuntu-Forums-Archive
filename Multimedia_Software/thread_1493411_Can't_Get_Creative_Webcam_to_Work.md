---
title: "Can't Get Creative Webcam to Work"
date: 2010-05-25
forum: Multimedia Software
---

### Post by jay3 on 2010-05-25
I have a Creative Labs webcam (model PD1110) and cannot get it to work with Ubuntu (in particular with skype).  I was running 9.10 and now on 10.04.  Any suggestions?

---

### Post by no2498 on 2010-05-26
910 and up cheese webcam booth is loaded
look in sound & video
try the cam in it first

if it does not come on

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

try the cam in cheese first


for skype open a terminal copy paste

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


hope this helps

---

