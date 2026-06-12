---
title: "No sound with Digigram VX222v2 and UbuntuStudio 10.04"
date: 2010-05-15
forum: Multimedia Software
---

### Post by ebrjvd on 2010-05-15
How can I get a Digigram VX222v2 soundcard working?
It did work with Karmic, but after reinstall with Lucid, the vx222 firmware appears to be missing.
AMD64 with UbuntuStudio 10.04, kernel 2.6.32-22-preempt.

I added "alsa-firmware-loaders" in Synaptic, but that seems insufficient.

The following files are present:

  /lib/modules/2.6.32-22-preempt/kernel/sound/pci/vx222/snd-vx222.ko
  /usr/src/linux-rt-headers-2.6.31-10/sound/pci/vx222/Makefile
  /usr/src/linux-headers-2.6.31-10-rt/include/config/snd/vx222.h
  /usr/share/doc/alsa-firmware-loaders/vxloader
  /usr/bin/vxloader

```

"aplay -l"
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


"cat /proc/asound/cards"
 0 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xfbefc000 irq 17


"lspci -v" 

04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
	Subsystem: ASUSTeK Computer Inc. Device 8210
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbefc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

05:07.0 Multimedia audio controller: PLX Technology, Inc. PCI9030 32-bit 33MHz PCI <-> IOBus Bridge (rev 01)
	Subsystem: Digigram Device 9c01
	Flags: medium devsel, IRQ 17
	Memory at fbfffc00 (32-bit, non-prefetchable) [size=128]
	I/O ports at ec00 [size=128]
	I/O ports at e800 [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-vx222, com20020-pci


"dmesg"
[    9.391440] Digigram VX222 0000:05:07.0: setting latency timer to 64
[    9.391518] Digigram VX222 0000:05:07.0: firmware: requesting vx/x1_2_v22.xlx
[    9.418537] vx: can't load firmware vx/x1_2_v22.xlx
[    9.418855] Digigram VX222: probe of 0000:05:07.0 failed with error -2


"vxloader"
vxloader: no VX-compatible cards found


```

How can I install the Digigram vx222 firmware?

---

