---
title: "[No sound from headphones] Board Asus A8N SLI Deluxe"
date: 2012-01-29
forum: Multimedia Software
---

### Post by Korn on 2012-01-29
Hello,

sound output with Ubuntu really seems still to be an adventure.

First the chaos from OSS to ALSA to PulseAudio and then the thousands of different flavors of the sound cards and chips. But anyway I have the opinion that every problem has a solution which is more or less comfortable ;)

Now to my problem: The situation is that I have a front panel on my PC which has an output for headphones and with Windows 7 the speakers are disabled once I plug in my headphones there. The sound only comes out of my headphones then which is exactly how I want it.

This behavior I would like to have with my great love Ubuntu, too. Here the situation is currently that plugging in my headphones has no effect at all. Neither my speakers are disabled nor is there any sound coming out from my headphones.

All important information about my ALSA system should be here: [http://www.alsa-project.org/db/?f=74acc34cf06acf788e8e2899c5a4be85940beb18](http://www.alsa-project.org/db/?f=74acc34cf06acf788e8e2899c5a4be85940beb18)

A summary of the (in my opinion) most important information:
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1b.0 0403: 8086:3b56 (rev 05)
Module: snd_hda_intel
Codec: VIA VT1828S
(The nVidia chip seems to be the HDMI output of my video card. Just ignore it.)

My mobo is the Asus A8N SLI Deluxe.

I was astonished that although the device is listed as an Intel chip the codec was identified as being from VIA.

After some research I started the snd_hda_intel module with the parameter model=generic which had the effect that I had quite sound in my headphones. Unfortunately I could not disable the speakers now separately because then the sound from my headphones was also disabled.

I thank everyone for comments and suggestion.

Korn

---

