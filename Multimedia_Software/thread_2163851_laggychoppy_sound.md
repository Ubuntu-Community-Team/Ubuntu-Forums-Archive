---
title: "laggy/choppy sound"
date: 2013-07-19
forum: Multimedia Software
---

### Post by feardotcom on 2013-07-19
So i cant seem to find any clue as to what is going on with my sound. I should first say that i run audio through hdmi.

When i play music sometimes the mp3 will get laggy or choppy. Best way to describe it is it sounds like a skipping record.

The issue also happens when watching a movie from an *.avi.

I has watched the system monitor while this happens and nothing seems to be spiking to cause the lag.

---

### Post by Yellow Pasque on 2013-07-20
You could try this: [https://wiki.ubuntu.com/Audio/PositionReporting](https://wiki.ubuntu.com/Audio/PositionReporting)

---

### Post by feardotcom on 2013-07-30
Ok, so i'm not using the intel drivers, it says GF106 in the sound settings because im running audio through hdmi. I tried the pulse audio solution and it still does not work. Any ideas?

---

### Post by SweetAurora on 2013-07-30
The GF106 uses the Intel Driver for audio. SND HDA Intel is the Linux equvilent to the Generic Sound Driver in Windows. So that link by Tem should work.

---

### Post by feardotcom on 2013-08-03
i tried all of those options and it's still skipping. Even on a fresh boot and not from a previous session it still skips. Any ideas?

---

### Post by SweetAurora on 2013-08-09
Lets try using the low latency kernel, it helps with audio and video problems.
```
sudo apt-get install linux-lowlatency
```
But read this before installing, the kernel isn't for everyone.
[http://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/](http://sevencapitalsins.wordpress.com/2007/08/10/low-latency-kernel-wtf/)

---

