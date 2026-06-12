---
title: "appropriate driver for webcam"
date: 2012-12-10
forum: Multimedia Software
---

### Post by icegood on 2012-12-10
Cannot find right one. My camera is
Bus 002 Device 002: ID 04f2:b1e5 Chicony Electronics Co., Ltd 
and it doesn't seem to be within 
[certified ones]("http://www.ubuntu.com/certification/catalog/make/Chicony%20Electronics%20Co.,%20Ltd/")

As result webcamera is inverted in all but cheese applications
(skype, kamerka, both different adobe flash plugins under
firefox (older one) and chrome).
How to fix it?

---

### Post by icegood on 2012-12-10
Clear, it should be driver issue.
It's just plugged [upside down]("http://www.ideasonboard.org/uvc/#footnote-3")
and should be recognized by libv4l automatically

---

### Post by curiosity on 2012-12-10
Hi, I had the same problem with Skype on my ASUS and here is the shortest solution (for Skype at least):

```
sudo gedit /usr/share/applications/skype.desktop
```then, in the line Exec=  :
```
Exec= bash -c 'LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype %U'
```In my case it worked. I have Ubuntu 12.04, for other version you may localize the file with:

```
localize v4l1compat.so
```and use the other path instead.

You can try to use the same command before running every other application which uses the webcam, but I didn't check that.

---

### Post by icegood on 2012-12-11
i wonder which library system found if v4l1compat.so wasn't pre-loaded first. In my case both kamerka and adobe flash (via [http://www.testwebcam.com/](http://www.testwebcam.com/) service) show inverted images even with preloading.

---

