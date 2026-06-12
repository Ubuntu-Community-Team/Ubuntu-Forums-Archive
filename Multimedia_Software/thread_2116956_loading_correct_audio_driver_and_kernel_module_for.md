---
title: "loading correct audio driver and kernel module for my HP g6  laptop sound card"
date: 2013-02-17
forum: Multimedia Software
---

### Post by arunkumar413 on 2013-02-17
Hi,

I have and AMD quad core HP g6 2006ax laptop with Dolby advanced auido and altec alnsing speakers on board. But the audio quality is good and volume level is not loud. The OS is ubuntu 12.04.

Please help me to load the correct sound driver and kernel module for my laptops sound card. The sound card information is as follows:

arun@ubuntu:~$ lspci -v | grep -A7 -i "audio"
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
	Subsystem: Hewlett-Packard Company Device 184a
	Flags: fast devsel, IRQ 18
	Memory at f0444000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel modules: snd-hda-intel

00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
--
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 184a
	Flags: bus master, slow devsel, latency 32, IRQ 16
	Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel

From the above output I think the amd audio device is being driven by an intel driver. that's why volume level is low and quality is not good.

---

### Post by Yellow Pasque on 2013-02-19
The correct driver (snd-hda-intel) is loaded. The system may have AMD APU, but the sound chip still uses Intel HDA specification: [http://en.wikipedia.org/wiki/Intel_High_Definition_Audio](http://en.wikipedia.org/wiki/Intel_High_Definition_Audio)

---

### Post by arunkumar413 on 2013-02-20
then what could be the reason for the low volume output.

---

