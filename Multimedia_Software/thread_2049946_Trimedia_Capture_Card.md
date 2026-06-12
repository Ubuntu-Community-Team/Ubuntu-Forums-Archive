---
title: "Trimedia Capture Card"
date: 2012-08-29
forum: Multimedia Software
---

### Post by cdicle on 2012-08-29
I have a frame grabber Flashbus Spectrim Lite, which probably nobody uses around. It has a philips/nxp chipset pnx1301EH. 

When I do lspci -vnn I get the output,

0c:02.0 Multimedia controller [0480]: Philips Semiconductors TriMedia TM1300 [1131:5402] (rev 83)
	Subsystem: Device [4954:746c]
	Flags: bus master, medium devsel, latency 64, IRQ 5
	Memory at de000000 (32-bit, non-prefetchable) [size=16M]
	Memory at df400000 (32-bit, non-prefetchable) [size=2M]

I am not sure whether the driver is loaded or not and I can not get it work, say with VLC player or vgrabbj. 

any help appreciated.

---

