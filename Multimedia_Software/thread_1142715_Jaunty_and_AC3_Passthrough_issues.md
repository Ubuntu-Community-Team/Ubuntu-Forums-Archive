---
title: "Jaunty and AC3 Passthrough issues"
date: 2009-04-29
forum: Multimedia Software
---

### Post by RDV on 2009-04-29
Since Ubuntu added pulseaudio upgrading to a new Ubuntu release has always brought with it issues with AC3 passthrough on my SPDIF connection. Each time I need to disabled pulseaudio. Three releases (8.04, 8.10 and 9.04).

The MythTV frontend (at least in trunk v0.22) will not even start if pulseaudio is running.

When I upgraded to 8.10 I finally got things working but had to exchange Amarok for Rhythmbox before both PCM and AC3/DTS audio would worked hassle free.

After upgrading to Jaunty 9.04 and again disabling pulseaudio I have the following problem. After playing any PCM audio I cannot play AC3/DTS passthough. I have to restart the ALSA server. 

Getting audio to play properly should not be such as hassle between upgrades. Pulseaudio should be a choice rather than an imposition. Many people that want to use a media center attached to their sound system use a SDPIF connection and want their audio receive/processor to decode surround sound. 

Ubuntu has made it more difficult than necessary for a growing population of media center enthusiasts to use their distribution.

This is the third release that has wrecked my working audio setup. Each time costing me time and multiple system tweaks to get PCM and AC3/DTS audio working as I had before the last upgrade. I am not a happy camper Ubuntu.

Before anyone suggests it I have already reviewed and tried a number of solutions on the web an this forum.

---

### Post by kingmoffa on 2009-05-05
I've got a jaunty box thats a bit better for pulse audio support than it was with other releases.

SPDIF passthrough is working fine in most things for me. The build I have of mythtv (0.21) doesn't seem to support pulse (only alsa , jack , oss etc)

Audio works in myth , but changing vol doesn't. Myth is setup to use alsa and the vol controls show up and seem to move - just the vol doesn't change. 

My audio receiver is in another room and I use that to change vol currently, getting up to change the vol is so 1980s! lol - couch potato no more. 

In other apps that like pulse , the vol controls are fine. 

Will either compile svn myself or look for a pulse build of mythtv.

Now if only intel would sort their useless drivers out - video tearing ruining my myth experience. Nearly a year old major issue....

(Note to self - dont buy intel graphics anymore , nvidia although closed source actually work properly)

---

