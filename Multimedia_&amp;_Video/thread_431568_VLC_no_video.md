---
title: "VLC no video"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by dgel on 2007-05-03
Hi

I just installed Feisty and want to play my movies in VLC (since i don't like totem). Installation goes fine as well as opening the files and it starts playing the movies correctly.
However, if I try to skip parts of the movie or change the screen size, the screen goes black but my sound keeps going. Any ideas why this happens? and how to fix it?

Na-Fiann

---

### Post by jagolis on 2007-05-03
For the skipping, some video codecs/containers aren't the most friendly when it comes to being able to skip around, noteably .flv, .wmv, and broken .avi's (their indexes are stored at the end of the file I think.) If I required skipping/searching, I convert with ffmpeg first. Then it usually works.

---

