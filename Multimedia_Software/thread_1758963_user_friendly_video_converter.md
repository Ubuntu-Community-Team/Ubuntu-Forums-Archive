---
title: "user friendly video converter"
date: 2011-05-15
forum: Multimedia Software
---

### Post by upsla on 2011-05-15
[FONT=Arial Black]Hello 
Hi i am using Ubuntu 11.04 on my computer system.I urgently need a good video converter for converting videos.I have already installed FFmpeg and men-coder,Winff etc. The problem is each has its own drawback.For instance ffmpeg cannot convert a .avi to .3gp with audio working. My preferences are the converter should be user friendly, should support all popular video formats.

[/FONT]

---

### Post by no2498 on 2011-05-15
try tragtor

---

### Post by andrew.46 on 2011-05-16
> **upsla said:**
> For instance ffmpeg cannot convert a .avi to .3gp with audio working.

Well, actually FFmpeg *can* do that but perhaps your copy of FFmpeg as not been compiled to allow this. Choice of sound is usually amr or aac. Aac encoding can be added by following Fakeoutdoorsman's guide here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

This should allow you to create a 3gp file with h.263 video and aac sound, if you want amr FFmpeg can be built against libopencore-amr.

---

