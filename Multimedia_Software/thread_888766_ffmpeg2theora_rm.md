---
title: "ffmpeg2theora rm"
date: 2008-08-13
forum: Multimedia Software
---

### Post by bobotoes on 2008-08-13
Is there some way to convert a real video file (.rm) using ffmpeg2theora? My attempts are unsuccessful. The result is a .ogg file that plays the audio portion but no video.

---

### Post by andrew.46 on 2008-12-27
Hi bobotoes,

> **bobotoes said:**
> Is there some way to convert a real video file (.rm) using ffmpeg2theora? My attempts are unsuccessful. The result is a .ogg file that plays the audio portion but no video.

The problem is that ffmpeg2theora uses ffmpeg to *decode* video and then libtheora to *encode* it. So I suspect in your case your copy of ffmpeg cannot deal with .rm files. (Itn fact I am not entirely sure that ffmpeg can deal with these?)

Can you convert your .rm files to a format that ffmpeg understands?

Andrew

---

