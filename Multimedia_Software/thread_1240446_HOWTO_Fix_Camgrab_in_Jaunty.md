---
title: "HOWTO: Fix Camgrab in Jaunty"
date: 2009-08-14
forum: Multimedia Software
---

### Post by zerhacke on 2009-08-14
In a terminal or with Synaptics or whatever your package manager of choice is, install the following

libv4l-0
libjasper1
libjasper-dev
libjasper-runtime

Then with your favorite camera software, launch in the terminal with the following LD_PRELOAD

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so camgrab

The above will launch camgrab with the v4l compatibility camgrab and almost every other webcam software for Jaunty needs.

---

