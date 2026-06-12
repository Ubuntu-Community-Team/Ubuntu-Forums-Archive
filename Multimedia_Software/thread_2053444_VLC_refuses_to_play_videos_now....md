---
title: "VLC refuses to play videos now..."
date: 2012-09-05
forum: Multimedia Software
---

### Post by CinoxFellpyre on 2012-09-05
Title says it all. Reinstalling does not help.

The logs I get from terminal are from playing an .avi file.

```
[0x8f1c914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1346850235)
Warning: call to rand()
Warning: call to srand(1346850235)
Warning: call to rand()
Warning: call to srand(1346850235)
Warning: call to rand()
Warning: call to srand(1346850235)
Warning: call to rand()
Blocked: call to setlocale(6, "")
[mpeg4 @ 0x959f9e0] Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x9511380] Invalid and inefficient vfw-avi packed B frames detected
libva: libva version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/i965_drv_video.so
libva: va_openDriver() returns -1
[0x95e81e4] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
[0x95e81e4] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
[0x95e81e4] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)
[0x95e81e4] avcodec decoder error: more than 5 seconds of late video -> dropping frame (computer too slow ?)

```

---

### Post by Epodx64 on 2012-09-07
What kind of Video card are you using?

---

### Post by CinoxFellpyre on 2012-11-21
> **Epodx64 said:**
> What kind of Video card are you using?
Um, the video card has nothing to do with it since I can play it perfectly fine in GNOME player.

---

