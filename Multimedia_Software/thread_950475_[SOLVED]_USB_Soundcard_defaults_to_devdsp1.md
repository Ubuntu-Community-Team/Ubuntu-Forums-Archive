---
title: "[SOLVED] USB Soundcard defaults to /dev/dsp1"
date: 2008-10-17
forum: Multimedia Software
---

### Post by Toet on 2008-10-17
I have a USB soundcard, and it is set as /dev/dsp1. This is not to my likings, as a lot of programs use /dev/dsp0 or hw:0,0 as their device.

I do not have a /dev/dsp0. How can I make my USB soundcard to be /dev/dsp0?

---

### Post by Toet on 2008-10-17
Solved, in the alsa-base file my snd-usb-audio was prevented to take the first sound slot. Commented that line out.

---

