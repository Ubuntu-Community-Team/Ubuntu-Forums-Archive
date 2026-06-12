---
title: "Kaffeine won't play since update."
date: 2009-11-03
forum: Multimedia Software
---

### Post by jfinner1 on 2009-11-03
I updated to Karmic, and now none of my videos will play in Kaffeine. I try to open a video, of any sort, DVD, avi, flv, and nothing happens. This new update really hates me... Any ideas??

---

### Post by jfinner1 on 2009-11-03
Ok, it's worse then I thought. Nothing will play in VLC, Kaffeine, or Totem. I get sound but no video in MPlayer, Video but no sound in MoviePlayer, and Banshee just crashes. Avidemux can't initialize the audio. Basically, there isn't a program that I can think of that will allow me to play movies on this computer right now. I really hope I can find a fix for this. If not, I'm moving back to Jaunty.

---

### Post by jfinner1 on 2009-11-05
bump

---

### Post by mtron on 2009-11-09
to fix kaffeine 1.0 pre try:

```
sudo apt-get install libxine1-all-plugins phonon-backend-xine
```

---

