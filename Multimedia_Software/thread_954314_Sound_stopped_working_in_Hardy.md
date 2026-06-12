---
title: "Sound stopped working in Hardy"
date: 2008-10-21
forum: Multimedia Software
---

### Post by cov on 2008-10-21
Hi,

I have carefully followed the 'Comprehensive Sound Guid' sticky to no avail.

My sound suddenly stopped working.

'aplay -l' produces the following
```
root@Gimli:/home/dave# aplay -l
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

```
Relevant response from 'lspci -v':```

00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
	Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Unknown device 3585
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 3
	I/O ports at e300 [size=256]
	I/O ports at e400 [size=128]
	Memory at ef001000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
02:06.0 Multimedia audio controller: Creative Labs SB Audigy LS
	Subsystem: Creative Labs SB0410 SBLive! 24-bit
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d000 [size=32]
	Capabilities: [dc] Power Management version 2

```

'lsmod -l snd-*' response includes:
```
/lib/modules/2.6.24-19-generic/updates/alsa/pci/ca0106/snd-ca0106.ko
/lib/modules/2.6.24-19-generic/updates/alsa/pci/ac97/snd-ac97-codec.ko

```

Alsamixer is not muted.

(Incidently, while playing around with the 'mute' in alsamixer I caused my wifi to stop responding which tends to indicate to me that there is a hardware conflict)

---

