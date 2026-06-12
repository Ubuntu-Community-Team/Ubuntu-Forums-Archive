---
title: "where is multiface_firmware.bin ?"
date: 2009-11-16
forum: Multimedia Software
---

### Post by gorgon on 2009-11-16
Hi there,

I need to get my RME Multiface soundcard working in 9.04. When I try to load 'hdsploader' it cant find the binary. 

gorgon@ubuntu:~$ hdsploader
hdsploader - firmware loader for RME Hammerfall DSP cards
Looking for HDSP + Multiface or Digiface cards :
Card 0 : HDA Intel at 0xfe020000 irq 17
Card 1 : RME Hammerfall DSP at 0x40000000, irq 16
Upload firmware for card hw:1
Unable to open file '/lib/firmware/hdsploader/multiface_firmware.bin' for reading

And looking for it with 'locate multiface_firmware.bin' gives no result.

Ive got alsa-firmware-loaders v. 1.0.18-1ubuntu2

Any ideas?

cheers,
g

---

### Post by diesch on 2009-11-16
Seems to be in [Medibuntu's alsa-firmware](http://packages.medibuntu.org/jaunty/alsa-firmware.html)

---

### Post by gorgon on 2009-11-17
thanks, that did the trick. very odd that the binary is not in the same package as hdsploader.

---

### Post by diesch on 2009-11-18
There may be legal issues with distributing the firmware in some countries.

---

