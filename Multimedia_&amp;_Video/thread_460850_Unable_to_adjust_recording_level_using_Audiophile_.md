---
title: "Unable to adjust recording level using Audiophile M2496 Card"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by bananabob on 2007-06-01
Preferences>Sound>Sound Capture  set to *ALSA - Advanced Linux Sound Architecture*
Preferences>Sound>Device set to *M Audio Audiophile 24/96 (Alsa Mixer)*

Audacity>Edit>Preferences>Recording>Device set to ALSA: [I]M Audio Audiophile 24/96: ICE1712 multi (hw:0,0)
[/I]
> 
alsarecord -l
**** List of CAPTURE Hardware Devices ****
card 0: M2496 [M Audio Audiophile 24/96], device 0: ICE1712 multi
[ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Using alsamixer -V capture
I discover have two capture "channels" to choose from 
either IEC958 or
H/W Mult 

The problem is that I can not change the recording level in Audacity at all even with both of these set "not to capture" (that is there is no red CAPTUR beneath them only ------), the recording level is still way too high.

This problem stated when I upgraded to Feisty.

---

