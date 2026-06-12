---
title: "Audigy SE in Ubuntu 8.04.1, sound not working"
date: 2008-10-22
forum: Multimedia Software
---

### Post by loaded123 on 2008-10-22
I can't seem to get my sound working correctly. Videos work (although with no sound), but the sound does not.  I did mess around with the volume controls and got a test sound to play after testing the different devices in the list, so I think the sound is working somewhere. I think the problem is that ubuntu is trying to use my onboard sound instead of the sound from my sound card. Does anyone know what I can do to fix this? Thanks for the help.

loaded

---

### Post by loaded123 on 2008-10-22
Oh and my sound card does seem to be detected. This is what I get:

dennis@dennis-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

dennis@dennis-desktop:~$ lspci -v

.
.bunch of random stuff here, then
.
02:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs Unknown device 100a
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at 9c00 [size=32]
	Capabilities: <access denied>

---

### Post by markbuntu on 2008-10-23
If your Creative Audigy card on is not giving you any sound, make sure the analog/digital check box in your sound mixer is unchecked.

---

### Post by loaded123 on 2008-10-27
I got it fixed. I just had to disable my onboard in the BIOS and do a new fresh install and everything works fine now.

---

