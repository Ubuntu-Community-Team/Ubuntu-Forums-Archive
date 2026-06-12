---
title: "Ekiga-gtkonly: Could not open audio channel for audio reception"
date: 2008-12-02
forum: Multimedia Software
---

### Post by jis on 2008-12-02
The error in question happens when I answer a call or when the other party answers a call:
> An error occured while trying to play audio to the soundcard for the audio reception. Please check that your soundcard is not busy and that your driver supports full-duplex.
The audio reception has been disabled.

How do you check, if the driver supports full-duplex? This is in ubuntu 8.10. I succeeded calling by same hardware in ubuntu 8.04; maybe it was ekiga instead of ekiga-gtkonly, though.

In terminal:
> $ lspci | grep audio
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)


---

