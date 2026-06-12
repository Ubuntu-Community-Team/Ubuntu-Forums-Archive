---
title: "No Sound snd-hda-intel ALC888"
date: 2009-04-30
forum: Multimedia Software
---

### Post by treezrppl2 on 2009-04-30
hey guys. my apologies, i'm a complete newb (i started using Ubuntu 2 weeks ago, just before jaunty release), but i'm having a heap of trouble with my audio.

i'll start off with specs. i've got an ALC888 RealTek audio chip on a Gigabyte EX58-UD3R
(i should also note that i have an ATI RADEON HD 3870 which caused me a heap of issues with my windows install but i've finally gotten that one working)

so back to the issue. i get no sound at all. i've been through quite a few forums with varying advice, none of which worked, so i'll just ask in my own thread. i've installed (or attempted to) drivers from both ALSA and RealTek. i've cranked all levels to max in gnome-alsamixer (and made sure they were unmuted). and edited both /etc/modules and /etc/modprobe.d to (i think) include the drivers.
EDIT: also, when going to System>Pref.>Sounds, testing anything but "HDA Intel ALC888 Digital (ALSA)" returns:
> audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open audio device for playback.
i found a script on the ALSA website to compile a bunch of my specs into one sheet so i can just say "look here" so, if you can help via that sheet. it's below.

_**TL;DR?**_ - _**NO AUDIO. HALP!!!**_
[http://www.alsa-project.org/db/?f=93a5f6ff211a45c6f5ed5ea32c4168efc7436404](http://www.alsa-project.org/db/?f=93a5f6ff211a45c6f5ed5ea32c4168efc7436404) 

thanks in advance

---

### Post by treezrppl2 on 2009-05-01
Sound is now _functional_ thanks to pulse-audio...
but it's a bit low for Volume, and if i turn it up a bit, the sound quality starts taking a dive. white-noise etc. perhaps it's just the drivers.

---

