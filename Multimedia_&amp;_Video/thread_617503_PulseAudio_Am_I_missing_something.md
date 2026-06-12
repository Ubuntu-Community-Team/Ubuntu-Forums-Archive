---
title: "PulseAudio: Am I missing something?"
date: 2007-11-19
forum: Multimedia &amp; Video
---

### Post by bnemesis on 2007-11-19
So I decided to reformat my ubuntu partition, and start fresh after having a ton of sound issues trying to get the Mumble voice chat working.

This time around, I have decided to use PulseAudio instead of ESD.  I get system sounds, and apps like Audacious, but I do have some glaring issues.

1) Audacious (using the pulseaudio plugin) is the only app that I can control audio on.  Everything else is either at max volume, or muted all the time no matter what the mixer controls are at.

2) In wine, there is no ALSA PCM device and choosing OSS no longer produces sound. Choosing ESD produces sound in games, but is slow.

3) None of the inputs are working (no microphone, etc).

My sound chipset is an onboard SIS SI7012.  Anyone know if I am missing a setting for making volume controls work?

---

