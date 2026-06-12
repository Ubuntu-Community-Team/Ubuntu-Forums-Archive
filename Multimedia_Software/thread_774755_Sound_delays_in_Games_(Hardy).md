---
title: "Sound delays in Games (Hardy)"
date: 2008-04-29
forum: Multimedia Software
---

### Post by BrownieBoy on 2008-04-29
With PulseAudio enabled in Hardy, my games (Quake 4 & Enemy Territory: Quake Wars) have a 2-3 second delay in all their sound effects, making them unplayable.  If I kill PulseAudio before starting the game, then the sound effects are back to normal.

No sound at all in Nexuiz, so far, even after killing PulseAudio.

This is a clean Hardy install, with an Audigy 2 soundcard.

These are all Linux native (i.e. not Wine) games.

---

### Post by BrownieBoy on 2008-05-01
Sound delays solved, in Quake 4 at least.  (Not tested any others yet).

I had to set the order of the sound devices in my /etc/modprobe.d/alsa-base file, by adding the following lines:

options snd-emu10k1 index=0
options snd-mpu401 index=1
options snd-intel8x0 index=2

The first line is my Creative Audigy 2 card.  Without these entries, ALSA must have been defaulting to one of the other, built-in sound options.

**Update**
This has fixed the problem in Quake 4 and Aliens Vs Predator Gold (Linux native).  However, Enemy Territory: Quake Wars Demo still has a delay, although it's not as bad as before: about a second behind, instead of three seconds.  Still makes the game unplayable.  Still getting no sound at all out of Nexuiz.

---

