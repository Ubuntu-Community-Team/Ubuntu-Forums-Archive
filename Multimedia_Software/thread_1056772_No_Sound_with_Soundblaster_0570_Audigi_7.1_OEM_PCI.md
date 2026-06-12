---
title: "No Sound with Soundblaster 0570 Audigi 7.1 OEM PCI"
date: 2009-02-01
forum: Multimedia Software
---

### Post by taronski on 2009-02-01
Still very new to Linux so please bear with me.  Installed 8.10 last week and checking if I can live for a couple of weeks without no MS at all at home. 

Just installed a SB OEM Audigy 7.1 PCI which I think the system can see

taron@Beast:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
taron@Beast:~$ 

I have tried to follow a number of trouble shooting guides to get it started with no luck, including the sticky thread.

I  sudo modprobe snd-ca0106 but still no sound through sound card (analogue jack is OK)

Not sure where to go from here...

Thanks

---

### Post by taronski on 2009-02-02
polite bump ;-)

Need to figure out if I need to RMA this card.

Thanks a lot

---

