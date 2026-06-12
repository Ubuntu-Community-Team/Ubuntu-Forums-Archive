---
title: "Multiple Sound Cards - Recording"
date: 2009-04-25
forum: Multimedia Software
---

### Post by kwagga on 2009-04-25
Heya Guys,

I'm about to pull my hair out, and I'm hoping someone could help save my hair.

I have two sound cards, Intel HDA ALC888 (OnBoard) and a PCI Creative Live! 24 Bit.

Firstly, both cards are working. The problem is, in sound preferences, I don't know which card is which, I want to assign the HDA card's mic to Sound Capture (and in Skype, etc) but it's not working. The HDA's output is being used by my desktop speakers, and the PCI card's output is for a headset, but that PCI card's MIC jack isn't working (I think) so thats why I'm using the HDA Mic port for the headset's mic, the other problem is that I can't get audio assigned to the headset (in Sound preferences) most likely because I don't know which option to choose.

I did however notice if I unmute the mic's in the sound manager, then I can hear the mic is working, but that is not desirable since the mic will broadcast to the speakers regardless of a program iow can't a program, i.e skype open the mic, and not also send it to the speakers?

One last thing, I'm a bit concerned over which sound system is really High Def with high sample rates, any recommendations?

My Options for playback are attached below.

[[img]http://www.freeimagehosting.net/uploads/th.2feeffe2f1.jpg[/img]](http://www.freeimagehosting.net/image.php?2feeffe2f1.jpg)


Some Other details:
user@user-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
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

Thanks for the help in advance... it's REALLY appreciated.

---

