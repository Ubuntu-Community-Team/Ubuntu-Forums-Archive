---
title: "Sony Vaio Sound Card Not Recognized"
date: 2010-05-02
forum: Multimedia Software
---

### Post by brolewis on 2010-05-02
I have recently installed Ubuntu 10.04 onto my Sony Vaio VGN-FJ170 laptop. Everything works great except for the sound card. Despite my best efforts, I cannot get the sound card to work. I have done numerous searches and have tried a number of solutions from the "Comprehensive Sound Problem Solutions Guide" thread but to no avail.

As suggested by several threads, I have reproduced the output from aplay and lspci below:

 lewis@parishmedia:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****

lewis@parishmedia:~$ lspci -v
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High
 Definition Audio Controller (rev 03)
	Subsystem: Sony Corporation Device 81f1
	Flags: bus master, fast devsel, latency 0, IRQ 24
	Memory at b0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 
Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

While the sound card seems to be found, nothing recognizes the sound card and therefore it is not used. Reinstalling the packages hasn't helped, messing with alsamixer hasn't helped, even installing drivers from source didn't help. I have come to my wit's end and am uncertain where to head next. Does anyone out there have any suggestions?

---

