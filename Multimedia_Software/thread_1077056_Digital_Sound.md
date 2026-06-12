---
title: "Digital Sound?"
date: 2009-02-22
forum: Multimedia Software
---

### Post by neilevan814 on 2009-02-22
Digital Sound on my asus M2N68-VM board??  Hi, My motherboard supports digital sound via the onboard sound chip, but when I typed in termial aplay -l It does not come up listed.  What can I do?

neil@neil-htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
neil@neil-htpc:~$

---

### Post by neilevan814 on 2009-02-22
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8345
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
	Memory at dfff8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

This is from lspci -v

---

