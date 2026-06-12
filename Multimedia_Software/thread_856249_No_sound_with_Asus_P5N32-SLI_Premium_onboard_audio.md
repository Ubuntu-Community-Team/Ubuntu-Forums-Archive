---
title: "No sound with Asus P5N32-SLI Premium onboard audio"
date: 2008-07-11
forum: Multimedia Software
---

### Post by mrshift on 2008-07-11
Hi,

I've been trying for months to get the audio on my Ubuntu rig back. I believe it worked *once* when I first installed Ubuntu, but not a peep since. Since then, for the life of me I cannot seem to find a suitable driver - I'm a keen amateur and liking Ubuntu, but I'll have to admit defeat with this soon! :)

Below are the responses back from the following commands:

**cat /proc/asound/cards**

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfe020000 irq 20
 1 [camera         ]: USB-Audio - USB camera
                      USB camera at usb-0000:00:0b.0-6, full speed

**aplay -l**

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**lspci -v**

00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
	Subsystem: ASUSTeK Computer Inc. Unknown device 81f6
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at fe020000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

Other than that, the system appears not to recognise the onboard audio as system beeps are made by the onboard buzzer - in other words, it's not just muted.

Thanks for listening!

---

### Post by mrshift on 2008-07-17
Anyone? [-o<

---

