---
title: "karmic gnome delta 1010lt audio"
date: 2010-02-06
forum: Multimedia Software
---

### Post by parisgraphics on 2010-02-06
hi,
i have a delta 1010lt sound card and used to have it running nicely via envy24 with ubuntu 8.04

i recently upgraded my machine to karmic and am having problems.
i've seen various posts - some saying that pulse audio is the problem and to remove it - others say pulse is ok. 

so i'm wondering if anyone has experience with this card on karmic and can share what works best.

here's what i know ....

1. cat /proc/asound/modules
gives
 0 snd_ice1712
 1 snd_via82xx

2. aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: M1010LT [M Audio Delta 1010LT], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

3. System->Preferences->Sound
 then going to the hardware tab, only shows the internal audio on my motherboard - not the 1010LT

Any advice appreciated!

---

