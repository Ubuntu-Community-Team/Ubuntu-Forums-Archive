---
title: "How to reduce background noise"
date: 2013-08-08
forum: Multimedia Software
---

### Post by satimis on 2013-08-08
Hi all,

With gnome-sound-recorder OR running following command;

```
ffmpeg -f alsa -i pulse -ar 44100 -ac 2 -ab 128k output.mp3
```

I can record sound as .mp3 file.  But there is a heavy background noise.   However if I lower the volume level of MIG on alsamixer I can reduce the noise.  But the sound recorded is also reduced.

Is there a solution?  Thanks

Rgds
satimis

---

