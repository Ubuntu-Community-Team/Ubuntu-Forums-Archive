---
title: "Maestro3 sound issue"
date: 2008-05-05
forum: Multimedia Software
---

### Post by flayedone on 2008-05-05
I feel as if I have searched every last corner of the Earth for a solution to my problem.  I haven't found anything that has fixed my problem yet.  Here is the deal:

Dell Inspiron 4000
Meastro3 sound card
Xubuntu 8.04
uname -r
2.6.24-16-generic

Sometimes the sound works, sometimes it doesn't.
When it doesn't:
dmesg

(this next line is displayed many times)
ALSA /usr/src/modules/alsa-driver/pci/maestro3.c:1930: ac97 serial bus busy
ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:2070: AC'97 0 access is not valid [0xffffffff], removing mixer
ACPI: PCI interrupt for device 000:00:08.0 disabled
Maestro3: probe of 0000:00:08.0 failed with error -5

That was the important stuff.

The problem is that this doesn't happen everytime, sometimes everything boots fine, no ALSA problems and my sound works, however, I can't find any rhyme or reason for it.

So far I have complied all the ALSA stuff twice with module assistant, created and messed around with /etc/module.conf, entered sudo modprobe snd-maestro3 many times.  I even reinstall Xubuntu 8.04 to no avail.

I know the computer knows it's there because even with it doesn't work:
lspci
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)

however:
aplay -l
aplay: device list:205: no sound cards found...

alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory


The part that really gets me is that when it does work everything is fine, no dmesg problems and everything comes up with alsamixer and I can hear sound from the computer.

If more info is needed I'll be happy to provide it.
I'm at the end of the road, does anyone know anything about this?

---

### Post by alphasoup on 2010-10-23
Here we are years later and I have the same problem after
upgrading from 8.4 to 10.4.1.
Exact same card exact same error but in var log message, instead of -5 it is -2.

Issue happens all the time, the driver loads but the linkage to the physical card fails with -2.
Of course then alsa sees no device after that, no sound forever.
The same card works great with previous Ubuntu install.

It does look to me like the maestro3 driver has regressed and no longer supports this card version.
It would be nice though to be able to use the latest Ubuntu...

From lspci:
00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)

From messages:
Oct 23 07:59:02 ginus kernel: [ 6627.691732] Maestro3 0000:00:08.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
Oct 23 07:59:02 ginus kernel: [ 6627.691761] Maestro3 0000:00:08.0: firmware: requesting ess/maestro3_assp_kernel.fw
Oct 23 07:59:02 ginus kernel: [ 6627.757384] Maestro3 0000:00:08.0: PCI INT A disabled
Oct 23 07:59:02 ginus kernel: [ 6627.757430] Maestro3: probe of 0000:00:08.0 failed with error -2


The last line is the killer here.

---

### Post by alphasoup on 2010-10-31
The maestro3 issue with 10.4.1 is resolved from loading from Synaptic package manager, for example: a recent kernel linux-386 (2.6.32.25.27), linux-backports-modules-alsa... and firmware 1.34.1. Not sure what is absolutely required but this combination fixed the problem while building alsa from source did not.

A great improvement for upgrade would be:
1) if upgrade completed without failure on this older hardware.
2) if then the correct firmware and alsa modules would be installed so that maestro3 would work the first time around.

---

