---
title: "sound glitch after upgrade to 10.10"
date: 2010-10-14
forum: Multimedia Software
---

### Post by farhoud.m7 on 2010-10-14
hi
after upgrade my ubuntu 10.4 to 10.10 mp3's and videos play with lag and use too much system source.
i tested totem vlc and mplayer and no luck.
how can i fix it?

---

### Post by olivair on 2010-10-29
Hy!

I have the same problem after installing the new Ubuntu 10.10. All media players lag, the built-in media player, youtube etc. even on normal videos, but my machine have the hardware to play FullHD videos(It worked smoothly on 10.04 Lucid). I noticed that rhythmbox works well, that is the only exception. I installed the latest kernel, but it didn't solve the problem. I can't find solution on any forums...If someone know something about it, please tell us! It's really annoying

Thanks

---

### Post by herophuong on 2010-10-31
This is a problem with pulseaudio server.
There are 2 solutions:
1) You can remove the pulseaudio config file: 
> rm -r ~/.pulse ~/.pulse-cookie 
2) Remove pulseaudio and use only alsa. (I think this way is better)

---

