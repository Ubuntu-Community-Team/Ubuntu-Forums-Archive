---
title: "FFMpeg for xbox 360"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by chedabob on 2006-11-05
Has anybody successfully used FFmpeg to create a video file that can be put on a USB stick and read by the 360? Ive tried it with -vcodec wmv1, -vcodec wmv2, and without anything, just an output as a .wmv. The 360 can see them, but says they are unplayable.

---

### Post by MegaFrame on 2008-05-13
Using a USB stick device it needs to be Fat 16/32 formated, NTFS drives don't work from what I've tried. For the encoding I've been using MEncoder which uses the libavcode library (from ffmpeg). I posted most of the info on the transcoding process here [wiki.megaframe.org Transcoding : MEncoder]("http://wiki.megaframe.org/index.php/XBOX_360_with_Linux_%28Ubuntu%29_Media_Share#Transcoding_:_MEncoder") Still need to add some info on using fuppes on there but thats most of the info on the transcoding I collected from various forums and sites.

---

