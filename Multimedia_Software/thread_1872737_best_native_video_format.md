---
title: "best native video format"
date: 2011-10-31
forum: Multimedia Software
---

### Post by geoffDeGeoffGeoff on 2011-10-31
I am building a website for somebody who wants people to be able to download some videos to play later.
They will offer wmv for win, mov for mac - what is the best format to offer for linux users?  I am after a video format that will work out of the box with no need to download any codecs etc

Ta

---

### Post by aeiah on 2011-10-31
ogg theora

---

### Post by FakeOutdoorsman on 2011-10-31
> **aeiah said:**
> ogg theora
FFmpeg example:
```
ffmpeg -i input -vcodec libtheora -acodec libvorbis -qscale 6 -aq 3 output.ogv
```
[list]
[*]**qscale:** Video quality. Higher number is higher quality. Range is 1 to 10 I believe.
[*]**aq:** Audio quality. Higher number is higher quality. Range is probably -1 to 10.
[/list]
The qscale values for libtheora and the aq values for libvorbis do not necessarily apply to other, external encoding libraries.

---

