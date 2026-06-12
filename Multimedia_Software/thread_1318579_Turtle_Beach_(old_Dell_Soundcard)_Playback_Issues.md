---
title: "Turtle Beach (old Dell Soundcard) Playback Issues"
date: 2009-11-07
forum: Multimedia Software
---

### Post by agent20x on 2009-11-07
One of my roommates wanted to check out the latest version of ubuntu, so I gave him the cd (9.10) and he installed it. Works fine until we tried to play some videos or pandora. The sound is barely understandable. If you play around with the volume level sometimes you can get the screeching to go away.

He has some funky Turtle Beach Santa Cruz card (never even heard of the company personally). I found a thread that suggested turning off power save and changing the sampling rate of pulse audio, but the power save thing did nothing and changing the sample rate made it worse.

I tried the Live CD for 9.04 and the sound works fine. Is there some way to install the 9.04 sound drivers (if that is even the problem) on 9.10?

---

### Post by AW36 on 2009-11-08
I have the exact same problem. Worked on 9.04, but when i updated to 9.10 it messed up.

specs:
Dell Dimension 8200
1.9ghz p4
256 mb ram
nvidia geforce2 Mx400
40 GB WD IDE drive
Turtle beach santa cruz sound card, chipset CS4630

any help appreciated :)

---

### Post by AW36 on 2009-11-08
bump

---

### Post by dano1 on 2009-11-09
had a santa cruz, no luck with 9.04.  Check alsa homepage for supported chipsets but its a 10 year old + card.

---

### Post by jcharpak on 2009-11-25
You're encountering [bug 428619]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/428619") no fix has been announced

---

