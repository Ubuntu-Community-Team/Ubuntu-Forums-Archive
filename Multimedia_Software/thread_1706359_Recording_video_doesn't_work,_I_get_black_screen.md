---
title: "Recording video doesn't work, I get black screen"
date: 2011-03-13
forum: Multimedia Software
---

### Post by zrbq on 2011-03-13
Hi. When I try to record video with the built-in webcam on my Acer netbook, I get a black screen with no audio as the result in Cheese. In Kamoso, I used to get super-sped-up recording, but now it seems not to work at all. In PiTiVi, the option for recording via webcam is greyed out.
Does anybody know of an alternative application I can try, or perhaps a solution to fix one of the applications above?

I am running Lucid Lynx. The camera is listed in "lsusb" as "Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera"

---

### Post by yax51 on 2011-03-14
yeah I'm getting the same thing, my web cam is detected, but I only get a black screen. It was working fine about 3 days ago, but nothing now.....

Asus G50vt
Bus 002 Device 004: ID 04f2:b012 Chicony Electronics Co., Ltd 1.3 MPixel UVC Webcam
Maverick Meerkat

---

### Post by no2498 on 2011-03-14
open a terminal type gstreamer-properties click enter
click video try v4l and v4l2 use the bottom test button for each 1
you may need to set the plugin to auto
stay in this till you see the cam come on

---

