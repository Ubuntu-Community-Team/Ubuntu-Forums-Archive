---
title: "Sound card not recognized"
date: 2008-04-28
forum: Mythbuntu
---

### Post by jakep_82 on 2008-04-28
I'm having trouble with sound in Mythbuntu 8.04.  I've been running Arch on my myth box for quite some time but I've grown tired of the constant management and I'm attempting to switch to Mythbuntu.

Everything appears to work right out of the box except sound.  I have an Asus M2V mobo and support for digital sound output was added in ALSA 1.0.15.  It works fine when I run Arch on the system.  Mythbuntu appears to be attempting to use the sound out on one of my Kworld ATSC-110 cards (alsamixer says SAA7134).  Should I run alsaconf to fix this?  If so, what package contains alsaconf?  It doesn't seem to be included with the default install.  Any help is appreciated.

Thanks,
Jake

---

### Post by klc5555 on 2008-04-28
asoundconf ought to be what you need.

First "asoundconf list" to get a list of your alsa devices, including the ones on your capture cards.

Then "asoundconf set-default-card <<whatever the alsa device is on your motherboard>>" to get alsa using the correct device.

---

### Post by jakep_82 on 2008-04-29
I figured it was something simple.  Thanks for the help.

---

