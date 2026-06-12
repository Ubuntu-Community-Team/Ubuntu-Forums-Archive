---
title: "Garbled screen with INTEL graphics"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by ashrack on 2006-06-10
have the following onboard VGA card:
```
0000:00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02) (prog-if 00 [VGA])
	Subsystem: Intel Corporation D815EGEW Mainboard
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 11
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Memory at ffa80000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [dc] Power Management version 2
```

And in XORG its set as i810.
At times when I move the mouse to a corner I get a garbled screen. Its like the whole screens turn into green and dark green cubes. And nothing else is visible. And to get out of this garbled screen a user just must move the mouse for a period of time to get the normal screen back.

This happens in all resollution with 16bit graphic.
I also tried comenting out DRI and changing the driver to VESA. But with the driver set to vesa all I get is a black screen when GDM starts.
And I tried setting in XORG.CONF  "NOACCEL"   "TRUE" but that also didnt help.
On this machine only 2D is needed(surfing the web, writting documents, chatin in aMSN)
What else could I do??

---

### Post by ashrack on 2006-06-11
bump

---

### Post by ashrack on 2006-06-16
bump

---

