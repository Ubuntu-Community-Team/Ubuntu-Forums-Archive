---
title: "Dual monitors ATI Radeon, 8.04"
date: 2010-02-02
forum: Multimedia Software
---

### Post by vikim on 2010-02-02
Dual monitors not detected in System->Screen Resolution.
Tried to add 2nd fglrx device manually to xorg.conf (per [1]).
No difference.
2nd monitor shows copy of the first. 
How can I configure dualmonitors ? 

[1] [http://ubuntuforums.org/showthread.php?t=158686](http://ubuntuforums.org/showthread.php?t=158686)
HowTo: ATI FGLRX Dual Monitor "Big Desktop" Mode

Attached:
 xorg.conf, 
 Xorg.0.log, 
 lspci.out

01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
	Subsystem: Giga-byte Technology Unknown device 2103
	Flags: bus master, fast devsel, latency 0
	Memory at 88100000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint IRQ 0

---

