---
title: "v4l2 loopback devices, ip cameras"
date: 2016-07-29
forum: Multimedia Software
---

### Post by cytg on 2016-07-29
I am not sure this is the right place, but here goes.

tldwr(too long dont wanna read) :
IP Cameras, Video4Linux2 loopback performance to /dev/videox.
Is it good?

Longer:
Developing my own video surveillance stack using ffmpeg, video4linux, sdl etc.
I want to setup a variable amount of cameras(ip cams, poe) if I can pull 20 cams+ that would be eeeexcellent.
I got working code capturing from webcam, it would be super fantastic if I could get the IP cameras streams to the same place ie. /dev/video0...n and I understand that is possible with a loopback and virtual device, however I would like not to loose too much latency(!) and not loose any frames.
So, any experience with the loopback functionality? Is it good, stable, fast? I have trouble googling up data on the combo, so here I am :).

Thanks for your time.

---

