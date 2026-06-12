---
title: "ffmpeg to re-encode x264 to divX"
date: 2010-03-22
forum: Multimedia Software
---

### Post by unterfuhrer on 2010-03-22
I need a re-encode a few x264 encoded movies to divX an my server and can't find how to do it with ffmpeg. Anyone than know?

---

### Post by FakeOutdoorsman on 2010-03-22
Here's a basic command to get you started:
```
ffmpeg -i input.mp4 -acodec libmp3lame -ab 128k -vcodec mpeg4 -qscale 4 output.avi
```
You may consider adding the *-vtag DIVX* option if your player requires a specific [video FourCC](http://wiki.multimedia.cx/index.php?title=FourCC).

---

### Post by halj32 on 2010-03-22
or you can use the GUI version winff

---

