---
title: "Unable to change webcams fps"
date: 2013-12-26
forum: Multimedia Software
---

### Post by e-San on 2013-12-26
Hi!

I'm trying to load two webcams on one pc. Since it is an Wyse SX0 terminal and it is not very powerfull, i have problems with running two cameras at the same time (not enought bandwidth).
I'm unable to set up FPS other than 25 with VLC.
Any ideas?

comand:
```
vlc -I dummy v4l2:///dev/video2:width=320:height=240 --video-filter="rotate" --transform-type=90 --sout '#standard{access=http,mux=asf,dst=:8080}'
```

____________
I love Godzia.

---

