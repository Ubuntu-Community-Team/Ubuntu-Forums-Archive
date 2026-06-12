---
title: "Accidently Removed ATI Driver, Stuck in Low Graphic Mode"
date: 2009-02-17
forum: Multimedia Software
---

### Post by mgoblue on 2009-02-17
Hey, 

While following a guide to get my wireless to work, I ran this line:

```

sudo update-rc.d -f linux-restricted-modules-common remove


```

I'm pretty sure this removed the driver used for my video card.

From sudo lspci -v:

```


01:05.0 VGA compatible controller: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics] (prog-if 00 [VGA controller])
	Subsystem: Toshiba America Info Systems Unknown device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at cfdf0000 (32-bit, non-prefetchable) [size=64K]
	Memory at cfe00000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [50] Power Management version 3
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-


```

Does anyone know how I can get this driver back and get out of this low resolution/low graphics mode?

---

### Post by mgoblue on 2009-02-17
bump..

---

