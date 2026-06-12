---
title: "Screen corruption"
date: 2010-07-05
forum: Mythbuntu
---

### Post by lingenfr on 2010-07-05
One of the recent updates seems to have hosed my mythtv client. It starts fine and displays the menu (300x300). However, why I try to play a recording or go to live tv, I get a corrupted screen with wide vertical bars and normal sound. As for my video, lspci -v gives the following:

01:05.0 VGA compatible controller: ATI Technologies Inc RS690M [Radeon X1200 Series]
	Subsystem: ATI Technologies Inc Device 053a
	Flags: bus master, fast devsel, latency 64, IRQ 18
	Memory at f0000000 (64-bit, prefetchable) [size=128M]
	Memory at f8100000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at 9000 [size=256]
	Memory at f8000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel modules: radeon


I am running 64-bit lucid on my Everun Note with kernel 2.6.32-22-generic.

Any idea what is going on? Thanks.

---

### Post by lingenfr on 2010-07-25
Bump. Any help?

---

### Post by ian dobson on 2010-07-25
Hi,

If you search here you'll find quite afew threads about mythtv/ati/screen corruption.

Maybe try disabling composer? disable opengl in mythtv or try a different drive for your graphic card.

Sorry that I can't help you more than this, I've never used ATI cards on linux.

Regards
Ian Dobson

---

