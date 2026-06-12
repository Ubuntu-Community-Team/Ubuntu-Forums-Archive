---
title: "Realtek/nVidia sound not working after all &quot;successes&quot; in the sound solutions guide"
date: 2008-09-04
forum: Multimedia Software
---

### Post by oopsdude on 2008-09-04
Hi all,

I'm running Heron 64-bit with an on-board sound card, Realtek ALC861VD. I installed the driver from Realtek's site without a hitch, and it said that my mixer is alsa. I followed every step in the "Comprehensive Sound Solutions Guide," but still no sound output.

aplay -l:
> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC861VD Digital [ALC861VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


sudo lspci -v:
> 00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: Hewlett-Packard Company Unknown device 30e5
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
	Memory at c3020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping


sudo modprobe snd-hda-intel works fine (that seems to be the correct module). I'm confused, why is it using nVidia drivers? I have an nVidia video card, and the drivers for that also work fine. The rest of lspci is dominated by nVidia, so I'm wondering if maybe nVidia replaced my drivers with its own? I'm pretty lost here. Thanks for any help!

---

### Post by leepesjee on 2008-09-04
Hi oopsdude.
I don't know why its listed as NVidia, but it seems that the problems with your sound card are worked on:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220225](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220225)

---

### Post by oopsdude on 2008-09-04
That fixed it, thanks. Swear I never came across that post in several hours of looking. Thanks again!

---

