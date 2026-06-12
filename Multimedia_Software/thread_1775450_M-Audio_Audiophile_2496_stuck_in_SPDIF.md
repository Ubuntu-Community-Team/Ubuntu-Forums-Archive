---
title: "M-Audio Audiophile 2496 stuck in S/PDIF"
date: 2011-06-04
forum: Multimedia Software
---

### Post by astraljava on 2011-06-04
Hey all, 

if someone knows what to do it'd be greatly appreciated!

Here's the thing: my M-Audio Audiophile 2496 card is now stuck in S/PDIF In for Master Clock, after using it for routing signals from Behringer V-Amp Pro to its digital in.

I used it before, and faced the same problem, but managed to somehow get rid of it by tweaking alsamixer into all possible (and quite frankly some impossible) positions. But now, it just won't budge.

I was recommended to plug something in to the card, so envy24control would let me change the Master Clock, but to no avail.

I'm using Ubuntu Studio 11.04. I remember being able to switch back and forth in some much older releases, possibly 8.04. Not much help, is it. Just thought I'd share.

---

### Post by astraljava on 2011-06-08
Right, the issue was somehow resolved. Again, tweaked a lot of alsamixer settings, fumbled around mudita24 (tried installing it by hand when envy24control failed), connected an analog audio source (as per someone's recommendation). After several hours of desperate attempts, finally the master clock rate "let loose" and I was able to set it to 44.1 kHz.

Again, no idea what finally gave in. *shrug*

---

### Post by almark on 2011-09-12
> **astraljava said:**
> Hey all, 

if someone knows what to do it'd be greatly appreciated!

Here's the thing: my M-Audio Audiophile 2496 card is now stuck in S/PDIF In for Master Clock, after using it for routing signals from Behringer V-Amp Pro to its digital in.

I used it before, and faced the same problem, but managed to somehow get rid of it by tweaking alsamixer into all possible (and quite frankly some impossible) positions. But now, it just won't budge.

I was recommended to plug something in to the card, so envy24control would let me change the Master Clock, but to no avail.

I'm using Ubuntu Studio 11.04. I remember being able to switch back and forth in some much older releases, possibly 8.04. Not much help, is it. Just thought I'd share.

I've got this problem too, when I record from my digital tuner via the m-audio CO2 optical 2 coax interface, only way to get out of S/PDIF mode is to power down the CO2 and reboot, sounds like the good old windows 95 days. I'm using Ubuntu 11.04

---

