---
title: "New Asus MB no live tv audio"
date: 2008-07-24
forum: Mythbuntu
---

### Post by mark467 on 2008-07-24
Ok, I found out I had a bad MB in last system and built a  new one. I am now using an Asus P5gc-mx/1333 and cant get audio for live tv. I checked in alsamixer and it looks right. (It does look different than last one I had. MP3 plays fine. I can get TV audio if I turn on the line in under playback in alsamixer but it is the direct feed that is delayed and stays on. Under capture I only have two options Input source which is set to line and a capture that I have adjusted the level on but no success. On another mb I had more options under capture

here is my lspci

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8290
	Flags: bus master, fast devsel, latency 0, IRQ 20
	Memory at d9ff8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Unknown type IRQ 0

Alasmixer says the chip is realtek alc662 rev1 if that matters

Any help would be appreciated. If you need more info let me know.

---

