---
title: "Have 4.0 sound with 2 outputs"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by Klaasvaak on 2008-04-20
I want to use both my computer speakers and my stereo speakers to create a sort of surround sound. In windows i succeeded by using eax. Now the only sound I am able to pour out of the rear speakers is when I do the following:

```

maarten@Fifi:~$ speaker-test -Dplug:surround51 -c4 -twav

speaker-test 1.0.14

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 4 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 32 to 16384
Period size range from 16 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
 3 - Rear Right
 2 - Rear Left

```

This indicates that they do work, but I still can't use them with programs like Exaile and VLC. How do I make these programs use my front and rear speakers simultaneously?

---

