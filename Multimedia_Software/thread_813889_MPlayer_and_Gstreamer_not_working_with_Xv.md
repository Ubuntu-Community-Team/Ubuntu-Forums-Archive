---
title: "MPlayer and Gstreamer not working with Xv"
date: 2008-05-31
forum: Multimedia Software
---

### Post by rahulthewall3000 on 2008-05-31
If the video driver is selected to xv in Mplayer preferences I fail to see the video. The error returned is that failed to initialize the selected -vo device.

Oh, and same with gstreamer output. X11 Window System (X11/XShm/Xv) also does not work and it says that Could not initialize Xv output?


Any ideas?

---

### Post by rahulthewall3000 on 2008-05-31
```
sudo dpkg-reconfigure xserver-xorg
```

I thought that solved the problem, but somehow the problem keeps reappearing on its own. As in, when I log in I Xv works, I play an mms stream over the internet, and then Xv stops working. Strange!

---

