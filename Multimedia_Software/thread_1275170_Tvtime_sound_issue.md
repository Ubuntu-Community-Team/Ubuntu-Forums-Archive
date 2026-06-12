---
title: "Tvtime sound issue"
date: 2009-09-25
forum: Multimedia Software
---

### Post by dianemeeks on 2009-09-25
I have, until now, been watching my tuner through tvtime, but streaming the sound through vlc with /dev/dsp2. A few days ago, this quit working. I still have sound elsewhere but not through vlc. After a few attempts I got white noise in both vlc and tvtime (this is the first time I've gotten anything through tvtime). I can't get the actual tv sound though. I'm not sure what info to post, but here goes.
dmesg | grep audio
[    8.608024] em28xx Doesn't have usb audio class
[    8.803526] AC97 audio (5 sample rates)
[    8.804304] tveeprom 1-0050: audio processor is None (idx 0)
[   10.538155] em28xx-audio.c: probing for em28x1 non standard usbaudio
[   10.538156] em28xx-audio.c: Copyright (C) 2006 Markus Rechberger

Any help would be great.
Thanks.

---

