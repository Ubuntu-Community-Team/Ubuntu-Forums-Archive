---
title: "convert .dv file to .mpeg"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by artvds2708 on 2007-11-30
How can I convert a .dv file to a .mpeg file ?
Is there a program for it ?
Or maybe even a command-line ?

---

### Post by eye208 on 2007-11-30
> **artvds2708 said:**
> How can I convert a .dv file to a .mpeg file ?
It depends on what type of MPEG you want.

For example, MPEG-4 H.264:
```
mencoder input.dv -ovc x264 -oac pcm -of rawvideo -o stream.h264
mencoder input.dv -ovc raw -oac mp3lame -of rawaudio -o stream.mp3
MP4Box -new output.mp4 -add stream.h264 -add stream.mp3
```

---

