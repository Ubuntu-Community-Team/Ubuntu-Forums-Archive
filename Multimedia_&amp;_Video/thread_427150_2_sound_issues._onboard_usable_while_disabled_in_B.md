---
title: "2 sound issues. onboard usable while disabled in BIOS, Audigy SE can't playback &amp; rec"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Zaggy on 2007-04-29
Situation:

I have onboard sound (via chipset) and an Audigy SE PCI card.
(ca0106 and via82xx)
I've disabled onboard sound in the BIOS.
However, I can still use it in Ubuntu Feisty!

I would like to use my Audigy SE, but I can't record & playback sound at the same time in Ubuntu Feisty.

Is there any way I can use my Audigy SE for both recording & playback of sound instead of my onboard?

I had to edit /etc/modprobe.d/alsa-base and put in the following lines to prevent Ubuntu Feisty from choosing a random card:

> options snd-via82xx index=0
options snd-ca0106 index=1

---

