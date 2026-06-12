---
title: "Hissing sound in 10.04"
date: 2010-06-28
forum: Multimedia Software
---

### Post by AussieGuy on 2010-06-28
First, sorry if I've opened up a new thread on an old topic.  But I've been reading heaps and haven't yet fund a solution.

I've not so long ago replaced an older (non-ubuntu) distribution on my desktop with Ubuntu 10.04.  All very nice and good - except for sound!  Now I know my hardware is fine, because sound worked fine before.  However, sound now hisses so much that it is effectively unworkable.

After much fiddling, and installing gnome-alsamixer, I can get a pretty good result if nearly everything is muted and IEC958 is unchecked - on headphones.  If I plug external speakers into the headphone jack, the sound is as hissy as before.  

I know this is (has been?) a common problem.  However, it is a matter of some urgency form me, as I need Skype to communicate with off-campus research students, and at the moment I can't.

For the record, here's the outcome of "aplay -l":

[FONT="Courier New"]**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/FONT]

and the relevant bits of "lspci -v":

[FONT="Courier New"]00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: Intel Corporation Device e002
	Flags: bus master, medium devsel, latency 0, IRQ 17
	Memory at febff800 (32-bit, non-prefetchable) [size=512]
	Memory at febff400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

02:00.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
	Subsystem: Ensoniq ES1371 [AudioPCI-97]
	Flags: bus master, slow devsel, latency 32, IRQ 21
	I/O ports at bc00 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371[/FONT]

In my old system, to enable sound I'd only enable Intel8x0, which seemed to work fine.  But even if I "sudo rmmod snd_ens1371" the hissing continues.

Any hints?

Thanks,
-A.

---

