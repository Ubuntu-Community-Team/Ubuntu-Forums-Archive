---
title: "Trying to preserve aspect ratio in mencoder"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by sfpiano on 2007-06-10
Here's the video I'm trying to encode:
VIDEO:  MPEG2  480x480  (aspect 2)  29.970 fps  6000.0 kbps (750.0 kbyte/s)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 480x480 => 640x480 Planar YV12 

Every time I run mencoder on this file the aspect ratio changes from 1.33 to 1

Here's the command I run:
mencoder 1048_20070116133000.mpg -o output2.mpg -ovc lavc -oac lavc -aspect 1.33

---

### Post by reclusivemonkey on 2007-06-21
Have you read this?

[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#aspect](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#aspect)

Might work for you...

---

