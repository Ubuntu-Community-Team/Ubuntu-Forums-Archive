---
title: "Avidemux: stuttering sound"
date: 2009-06-08
forum: Multimedia Software
---

### Post by jmjohn on 2009-06-08
Hey all,

I'm trying to edit a video made with the Flip Mino HD, which is an MP4 file in Avidemux.  

Problem: Sound stutters.  I've tried setting it to Alsa or OSS, but Pulse works best, it just stutters.  The stuttering borks the output when I try to convert it.

I've got the latest medibuntu packages...

Is there a good way to investigate the MP4 file to find out what might be the problem, like what sort of format is used in the container?

Thanks.

---

### Post by jmjohn on 2009-07-06
Found no good way to edit these AAC audio and AAV codecs inside an AVI container in Linux.  Cinellerra will do it, but that's just overkill.

I believe it has to do with some sort of relative frame referencing issue, if I remember correctly.

---

