---
title: "Can't play back 1280x720 video with MPlayer"
date: 2009-01-22
forum: Multimedia Software
---

### Post by jonno on 2009-01-22
My Panasonic camera takes 1280x720 video (jpeg stills in a .mov container). However I'm having trouble playing the video on my desktop. I get the following output when I try to play the video with mplayer -fs:
```
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12  [fs]
Source image dimensions are too high: 1280x720 (maximum is 1024x1088)
FATAL: Cannot initialize video driver.
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 3)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12  [fs]
Source image dimensions are too high: 1280x720 (maximum is 1024x1088)
FATAL: Cannot initialize video driver.

FATAL: Could not initialize video filters (-vf) or video output (-vo).
```

Why is it telling me the maximum resolution is 1024x1088? My screen resolution is set to 1280x1024 so that isn't the problem. Is it likely my video driver? I have the following on-board graphics:
Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device and I'm using the Intel driver.

---

