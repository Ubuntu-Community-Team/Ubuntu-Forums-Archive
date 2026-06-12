---
title: "Not detecting ipod on ubuntu 10.04 minimal"
date: 2010-09-16
forum: Multimedia Software
---

### Post by Ultra_Man on 2010-09-16
Neither Rhythmbox, Exaile, and Banshee detects the ipod. I have libgpod installed. 

I think the problem might be that for some reason I can't find the mount point of the ipod, but I can view the stuff inside the ipod on nautilus.

My iPod is running iOS 4.0.

---

### Post by r+9 on 2010-09-16
There is a package that was "blocking" my 1st Gen Shuffle, I will try to dig up the fix, it may not be what you're looking for though.

---

### Post by r+9 on 2010-09-16
[https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/565971](https://bugs.launchpad.net/ubuntu/+source/libgpod/+bug/565971)

found it.

sudo aptitude remove libgpod-common

again this was for an iPod Shuffle 1st generation ( 1GB ).

---

### Post by Ultra_Man on 2010-09-16
I don't think that's it, because now even nautilus isn't detecting the ipod.

---

### Post by Ultra_Man on 2010-09-17
Still having problems...

---

