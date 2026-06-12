---
title: "Which /dev/video* is which?"
date: 2007-08-01
forum: Multimedia &amp; Video
---

### Post by toallpointswest on 2007-08-01
I have a Logitech QuickCam and a Hauppage PVR-150MCE and as one would expect, I have /dev/video0 and /dev/video1 ... unfortunately when I do a cat /dev/video0 or a cat /dev/video1 all I get is garbage to the screen with no audio or video. How can I determine which video* is the right one for my tv card? Thanks all!

---

### Post by MrHippocampus on 2007-08-01
you could try checking the output of "dmesg" to see if it says anything about the /dev/video* nodes and which driver controls them

---

### Post by wolfen69 on 2007-08-01
i have the same card and mine is video0.

---

