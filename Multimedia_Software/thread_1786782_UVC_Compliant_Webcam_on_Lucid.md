---
title: "UVC Compliant Webcam on Lucid"
date: 2011-06-20
forum: Multimedia Software
---

### Post by sj1410 on 2011-06-20
Hi,

I have a usb cam which says its UVC Compliant. But anyhow it does not work on lucid.

If anybody is interested i can pay a good amount for the efforts required.

Please contact me at

swapnil <dot> indore <at> gmail <dot> com

---

### Post by no2498 on 2011-06-20
in a terminal type dmesg click enter
after it stops type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

now install guvcview try the cam in it

---

### Post by sj1410 on 2011-06-21
tried this and a lot more, its the same. The error can be summarized as v4l is not able to get or set any properties of the cam.

---

### Post by no2498 on 2011-06-21
they have all but stoped using v4l1 
there is a file called something like
v4l so v4l2  compat  ( convert )

i have only seen it 1 time it was on a skype thread

---

