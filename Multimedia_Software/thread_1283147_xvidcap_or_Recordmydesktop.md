---
title: "xvidcap or Recordmydesktop"
date: 2009-10-05
forum: Multimedia Software
---

### Post by JohnAvo on 2009-10-05
Kindly share your experience of using Linux screencasting tools. I am interested in fully automated solution to record a video from the screen and produce a small video file (flv preferred)

Thanks.

---

### Post by VertexPusher on 2009-10-05
VLC has a screen capture mode that is easy to use. If you need more options, use ffmpeg with the "-f x11grab" parameter. ffmpeg gives you full control over compression parameters, so you can capture high fps machinima with it as well.

I used RecordMyDesktop for a while, but its Theora output is hardly supported by video editors. I prefer to capture MJPEG in high quality, then edit and compress in a separate step.

---

