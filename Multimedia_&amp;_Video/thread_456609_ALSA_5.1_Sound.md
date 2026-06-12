---
title: "ALSA 5.1 Sound"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by JPhillips on 2007-05-27
I've managed to get most everything up and running (printing, sound, USB hd, etc.) However, I have a Creative 5.1 speaker setup that I really want to take advantage of and it seems to not be outputting in 5.1 by default. I can only hear sound out of my "front-left" speaker and I get bass from the sub. I'm pretty lost right now and any help would be appreciated.

Setup:
NVidia CK8S with ALC850 at irq 1
ALSA Version 1.0.14rc4

```
speaker-test 1.0.14rc4

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 3 to 5461
Period size range from 3 to 5461
Using max buffer size 5460
Periods = 4
was set period_size = 1365
was set buffer_size = 5460
 0 - Front Left //SOUND FROM FRONT-LEFT
 4 - Center //NO SOUND
 1 - Front Right //SOUND FROM FRONT-LEFT
 3 - Rear Right //NO SOUND
 2 - Rear Left //NO SOUND
 5 - LFE //NO SOUND
```

---

### Post by JPhillips on 2007-05-28
anyone?

---

