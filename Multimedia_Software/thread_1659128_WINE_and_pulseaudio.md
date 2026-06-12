---
title: "WINE and pulseaudio"
date: 2011-01-03
forum: Multimedia Software
---

### Post by foxmulder881 on 2011-01-03
What's the problem with WINE and pulseaudio?

Simple question really, but I'd like to run a running application through WINE and use pulseaudio yet there is no option to use pulse in the WINE config panel.

---

### Post by Yellow Pasque on 2011-01-03
IDK, the WINE devs seem resistant to pulseaudio. You can use ALSA or ESD in the WINE control panel. Pulseaudio will handle those just fine (in theory).

---

### Post by foxmulder881 on 2011-01-03
So what I'm wondering is, if I have set my pulseaudio config to output to 4.0 audio, will ALSA handle 4.0 too? Or do I also have to configure ALSA to output to 4.0?

---

### Post by Yellow Pasque on 2011-01-03
Try it and see..

---

### Post by foxmulder881 on 2011-01-03
> **Temüjin said:**
> Try it and see..

I'd have never have thought it would have worked by default using ALSA.

I done this:

```
chris@foxbox:~$ speaker-test -Dplug:surround40 -c4 -l1 -twav

speaker-test 1.0.23

Playback device is plug:surround40
Stream parameters are 48000Hz, S16_LE, 4 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 4 to 8192
Period size range from 4 to 8192
Using max buffer size 8192
Periods = 4
was set period_size = 2048
was set buffer_size = 8192
 0 - Front Left
 1 - Front Right
 3 - Rear Right
 2 - Rear Left
Time per period = 5.717153
```

And it worked. Thanks. ;-)

---

### Post by Yellow Pasque on 2011-01-03
Please mark thread SOLVED

---

