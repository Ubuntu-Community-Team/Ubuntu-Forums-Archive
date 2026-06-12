---
title: "HP dv6 Ubuntu 12.04.3 headphone jack not recognized by ALSA"
date: 2013-10-18
forum: Multimedia Software
---

### Post by Dxh3378 on 2013-10-18
Latest set of updates borked out my sound.  This had happened before and I was able to find a fix where I disabled Pulseaudio and just used the remaining ALSA.
But now, if I Terminal [alsamixer] neither the headphone jack or hdmi are in the list of outputs.

I have Googled this topic and found numerous threads, but I just don't know enough to tell if I am barking up the wrong tree or what.
Looking to fix output to both headphone jack as well as hdmi, and do some process that will prevent future updates from re-borking my sound.

Thanks 
D

---

### Post by Dxh3378 on 2013-10-18
[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Followed this and fixed the sound

---

