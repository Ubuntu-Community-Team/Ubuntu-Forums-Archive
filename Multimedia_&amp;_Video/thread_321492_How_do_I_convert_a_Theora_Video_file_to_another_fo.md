---
title: "How do I convert a Theora Video file to another format? AVI for instance?"
date: 2006-12-19
forum: Multimedia &amp; Video
---

### Post by hakimaki on 2006-12-19
How can I convert a theora video file to another format?  Format non-specific, avi, mpeg, etc...

---

### Post by pay on 2006-12-19
Do you want to convert the video with another codec or do you just want to change the container (ie avi, mkv, ogg) that the video is in?

---

### Post by hakimaki on 2006-12-19
The container.

---

### Post by pay on 2006-12-20
Well you could use the matroska container with mkvtoolnix. I'm not sure if theora and vorbis can go in a avi container but try```
mencoder /path/to/my.ogg -ovc copy -ova copy -o my.avi
```

---

### Post by hakimaki on 2006-12-28
Thanks for the advice, i actually have found luck in VLC.

---

### Post by timjayko on 2007-02-24
I am having same problem.. how do you use VLC to convert it.. all I can do right now is playback my video but i need to convert it

---

