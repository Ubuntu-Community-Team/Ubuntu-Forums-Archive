---
title: "Mplayer + ffmpeg"
date: 2008-11-17
forum: Multimedia Software
---

### Post by @H.264 on 2008-11-17
On Win Xp i used to use Mplayer classic in conjunction with ffmpeg.
On Ubuntu 8.10 i have Mplayer but i want to use ffmpeg ( installed ) as a decoder for wideo and audio.
My point is to have video decoded with latest ffmpeg.
How can "tell" to Mplayer to use ffmpeg for rendering videos?

---

### Post by andrew.46 on 2008-11-18
Hi,

The html docs suggest the -vfm option. For example:

```
mplayer -vfm ffmpeg movie1.avi
```

  Andrew

---

