---
title: "Ensoniq ES1371"
date: 2010-04-29
forum: Multimedia Software
---

### Post by W2IBC on 2010-04-29
since i got tired of the spurious response with the onboard hda-intel card. i disabled it and installed a old card i had laying around. i know the card works. but it wont on ubuntu

card is seen

00:08.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
	Subsystem: Ensoniq ES1371 [AudioPCI-97]
	Flags: slow devsel, IRQ 16
	I/O ports at ec00 [size=64]
	Capabilities: <access denied>
	Kernel modules: snd-ens1371

but aplay -l shows
aplay: device_list:223: no soundcards found...

i added the snd-ens1317 to /etc/modules

i try the modprobe snd-ens1371 and this is what i got

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

tryed alsamixer and this is what happens

ddog@NSA-59283:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory


any ideas?

---

### Post by W2IBC on 2010-04-30
also from dmesg

[   12.834276] ENS1371 0000:00:08.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.968292] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:704: es1371: codec read timeout at 0xec14 [0x40000000]
[   12.996252] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:704: es1371: codec read timeout at 0xec14 [0x40000000]
[   13.025868] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:644: codec write timeout at 0xec14 [0x40000000]
[   13.053761] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:644: codec write timeout at 0xec14 [0x40000000]
[   13.195300] lp: driver loaded but no devices found
[   13.247153] Disabling lock debugging due to kernel taint
[   13.252649] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   13.836228] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:704: es1371: codec read timeout at 0xec14 [0x40000000]
[   13.863843] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:704: es1371: codec read timeout at 0xec14 [0x40000000]
[   13.891896] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:704: es1371: codec read timeout at 0xec14 [0x40000000]
[   13.971185] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:704: es1371: codec read timeout at 0xec14 [0x40000000]
[   13.998353] ALSA /usr/src/modules/alsa-driver/pci/ens1370.c:704: es1371: codec read timeout at 0xec14 [0x40000000]
[   13.998359] ALSA /usr/src/modules/alsa-driver/pci/ac97/ac97_codec.c:2081: AC'97 0 access is not valid [0x0], removing mixer.
[   14.012067] ENS1371 0000:00:08.0: PCI INT A disabled
[   14.012095] ENS1371: probe of 0000:00:08.0 failed with error -5
[   14.212909] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.226294] ppdev: user-space parallel port driver
[   14.325247] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
[   14.325624]   alloc irq_desc for 17 on node -1
[   14.325627]   alloc kstat_irqs on node -1
[   14.325638] ndiswrapper 0000:00:09.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.326678] ndiswrapper: using IRQ 17

---

