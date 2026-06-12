---
title: "Old webcam don't work with OpenCV :("
date: 2009-08-12
forum: Networking &amp; Wireless
---

### Post by Repgahroll on 2009-08-12
Hello guys :).

I have a simple and old webcam branded a4tech, but the system says it's a:

0ac8:301b Z-Star Microelectronics Corp. ZC0301 WebCam

The problem is that i'm playing with webcam mouse tracking (ex.: [http://jacobandreas.net/2008/opencv-x-input/](http://jacobandreas.net/2008/opencv-x-input/)) i played a little on my netbook (ubuntu 9.04 unr) and now i want to play on my desktop, but the opencv examples that i compiled and that uses the webcam returns a segmentation fault, i tried preloading the v4l2convert and v4l1compat.so libraries before, for example:

PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/share/doc/opencv-doc/examples/c/camshiftdemo

I'm confused because a lot of tutorials talks about modules that don't seem to exist (on jaunty) anymore and i don't know what to do...

Is is possible to get it working?

My system is an updated Ubuntu 9.04 64-bit. The camera works with Cheese, Camorama (weird colours, preloading v4l1compat), Ekiga and Empathy, and don't work with Skiespea.

Thank you very much for your time.

---

### Post by Repgahroll on 2009-08-12
Please somebody move this topic to "Multimedia & Video" room.

---

