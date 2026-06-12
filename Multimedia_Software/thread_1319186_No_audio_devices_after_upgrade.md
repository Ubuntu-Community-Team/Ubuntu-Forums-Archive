---
title: "No audio devices after upgrade"
date: 2009-11-08
forum: Multimedia Software
---

### Post by Lucky75 on 2009-11-08
Hi all,

I seem to be missing my audio devices in System->Preferences->Sound under the hardware tab. Nothing shows up, and I have no audio. Please help :)

*Just upgraded to 9.10*

```

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

lspci -v

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Device 818f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at d8000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

I don't know if I should use pulse or alsa at the moment. Both are installed, but neither are working. I'd like to get simultaneous output working on a 5,1 system, preferably with flash/firefox as well. I always struggled with that.


Thanks!!


EDIT:

Here's a link to the state of my very confused system: [http://www.alsa-project.org/db/?f=548c69ec2a1d358cd8b2ffef2d456a6b1f79b488](http://www.alsa-project.org/db/?f=548c69ec2a1d358cd8b2ffef2d456a6b1f79b488)

---

