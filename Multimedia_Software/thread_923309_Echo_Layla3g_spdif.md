---
title: "Echo Layla3g spdif"
date: 2008-09-18
forum: Multimedia Software
---

### Post by efflux on 2008-09-18
I have a problem with this sound card. I'm wondering if anyone knows a solution. The card works and very well under Linux but in Jack the analog ins/outs work on hw:0 (the default or hw:0,0 and plughw:0). Then the spdif digital appears as hw:0,1. The spdif can only be used by selecting it seperatly with device hw:0,1. Then I lose all analogs. Anyone know if you can change this or how to set it up differently because spdif by itself is useless for audio production. I need to hook an external effect in via spdif. I don't think I ever tried using the spdif before so I don't know if any other changes to the Ubuntu system have effected it. I have used this card for a while but now I'm on Ubuntu 8.04.

I have tried various tweaking but at present the system is the same as a default 8.04 install (with added rt kernel) except that I had to compile and install the firmware.

The card also has MIDI, optical in/outs and software monitor mixing on the card. It has 8 analog/digital ins and 8 digital/analog outs. The echomixer software mixer is all functioning correctly.

 aplay -l outputs:

**** List of PLAYBACK Hardware Devices ****
card 0: Layla3G [Layla3G], device 0: Analog PCM [Layla3G]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Layla3G [Layla3G], device 1: Digital PCM [Layla3G]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7

---

