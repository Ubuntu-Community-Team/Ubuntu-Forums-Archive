---
title: "GeForce4 MX Integrated GPU compatibility?"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by kimusabi on 2006-08-07
Hello fellow Ubuntuer's.
I've just recently switched to Ubuntu 6.06 after using window's for many year's (Abit late, I know).
Although everything seem's to run fine and dandy, I do have a quetion regarding nVidia driver's. My hardware is quite old, but I still have the original installer disk for the driver's.

So I was wondering, with 6.06, will the driver's from the repositories work with my GeForce4 MX Integrated GPU?
If not, will I somehow be able to use the driver's from the driver CD?

Thank you so much (:
-Kimusabi

---

### Post by tseliot on 2006-08-07
It should work.

please try Method 1 of this guide:
[http://www.ubuntuforums.org/showthread.php?t=221313](http://www.ubuntuforums.org/showthread.php?t=221313)

---

### Post by kimusabi on 2006-08-07
I managed to fix it..apperently the normal nVidia-glx driver's work, you just have to change the etc/X11/xorg.conf "Driver" section from "nv" to "nvidia". Work wonder's now =D.

---

