---
title: "Broken headphones output -&gt; no sound on my speakers"
date: 2014-04-15
forum: Multimedia Software
---

### Post by peij on 2014-04-15
Hi everyone,

I can't get any audio output from my system.
It's a Mac Book Pro 8.2, with a Mint 16 system on it.

My headphones output is broken, and I can't take out the jack piece that is stuck in it.
In my sound config panel I've got 3 listening devices :
 - Digital Output (S/PDIF) [internal audio]
 - analog headphones [internal audio]
 - analog output [internal audio]

I tried to put evey volume slider at 100%, but still have no sound. Nothing is muted here.

I launched alsamixer to see how is it configured here, and my headphone volume is automatically set at 77 and the speaker level at 0.

But even if I change the level sliders here, I still got no sound from my speakers.

I also disabled the auto-mute mode in the alsamixer, but still the same.

I know that the speakers aren't physically disconneted, because if I boot on windows (what I don't want to do anymore), I can set up my output to the speakers, and they work well.

I thought about completely deactivate the headphones output, but I can't figure out how to do this.

[EDIT :]
Here is the output for 'aplay -l' :
> 
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: PCH [HDA Intel PCH], périphérique 0: CS4206 Analog [CS4206 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 0: PCH [HDA Intel PCH], périphérique 1: CS4206 Digital [CS4206 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 1: Generic [HD-Audio Generic], périphérique 3: HDMI 0 [HDMI 0]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0


Does anyone get any idea ?

Thank you in advance, and sorry for my english !

---

