---
title: "Support for pivoting monitors?"
date: 2006-09-18
forum: Multimedia &amp; Video
---

### Post by volfro on 2006-09-18
Hey guys,

I just bought a [Samsung Syncmaster 204b monitor]("http://www.samsung.com/Products/Monitor/LCD_Digital/LS20BRDBSQXAA.asp") which, of course, comes with Windows drivers but nothing for Linux.  It's installed and working nicely at full resolution, but there are some things missing here that are included for Windows.

One of the features of the monitor is that you can tilt it from landscape to portrait proportions, and the 'doze software that comes with it changes the image accordingly.

Is there any software that does that in Linux?  I haven't been able to find anything.

Also, is there any good color profiling/management available to Linux?  Again, I haven't been able to find any.

Thanks for any tips!!

---

### Post by volfro on 2006-09-20
Alright,

I figured out how to have the nvidia driver rotate the image for me, but it involves going into xorg.conf every time and adding the line ```
Option "Rotate" "CCW"
```
which is obviously a pain, because it involves restarting X every time I want the resolution to change from 4:3 to 3:4.

Does anybody know of a utility for GNOME that can do this for me, on the fly?

---

