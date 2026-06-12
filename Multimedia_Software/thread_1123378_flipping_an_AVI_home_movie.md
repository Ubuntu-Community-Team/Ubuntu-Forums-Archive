---
title: "flipping an AVI home movie"
date: 2009-04-12
forum: Multimedia Software
---

### Post by lightstream on 2009-04-12
Can anyone help me with flipping an AVI home movie? I took a video on my snowboard but was holding the camera upside down!

I've heard mencoder can do it, but I've had no luck with it so far.

Here's the command line I've tried, can anyone see anything wrong with it?

**mencoder -ovc copy -oac copy -vf flip MVI_0104.AVI -o MVI_0104_flipped.AVI**

It appears to work, happily outputting various messages about its progress, but the file it creates is not flipped.

Thanks in advance for any pointers, or another program that can do this if you can recommend one.

---

### Post by lightstream on 2009-04-12
OK, scratch that I solved it - basically you can't use **-ovc copy** if you want to apply a filter, I changed this to **-ovc lavc** and it worked great.

---

### Post by brunolabs on 2009-04-12
Try Cinelerra.

I think it does what you want (not sure though).

---

### Post by MartyBuntu on 2009-04-12
AVIDEMUX

Open the video in AVIDEMUX and then...
-video
-filters
-transform tab
-vertical flip

---

