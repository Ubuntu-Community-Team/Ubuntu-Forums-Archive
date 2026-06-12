---
title: "No TV on hardy heron"
date: 2008-06-07
forum: Multimedia Software
---

### Post by Tehriboy on 2008-06-07
Hi there,
I m using ubuntu (hardy heron) and recently installed mythtv using synaptic. My TV tuner is rather old since i m using it on my XP SP2 for 4 years. It is PV-M4500 PCI tv tuner card (Pixelview playtv pro 2)(BT878). 
When I m trying to run mythtv backend setup on capture card it shows 
Card info - analog v4l capture card
Video device - /dev/video0
probed info - BT878 video (*** UNKOWN/GENER [bttv]

after other settings whenever i run channel scan it could not find anything.
I've done a lot of googling round but nothing would help, as i said card works fine in xp sp2.

also after running tvtime-scanner again got no frequency.

the result of various commands are shown below -
dmesg (only relevent lines)
[   30.141238] Linux video capture interface: v2.00
[   30.618274] bttv: driver version 0.9.17 loaded
[   30.618282] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   30.618377] bttv: Bt8xx card found (0).
[   30.618410] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 21 (level, low) -> IRQ 22
[   30.618426] bttv0: Bt878 (rev 17) at 0000:05:00.0, irq: 22, latency: 32, mmio: 0x30001000
[   30.619398] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   30.619437] bttv0: gpio: en=00000000, out=00000000 in=009fc0ff [init]
[   30.620809] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   30.620814] bttv0: tuner type unset
[   30.620818] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   30.621449] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   30.622075] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   30.622747] bttv0: registered device video0
[   30.622782] bttv0: registered device vbi0
[   30.689287] bt878: AUDIO driver version 0.0.0 loaded
[   30.689352] bt878: Bt878 AUDIO function found (0).
[   30.689378] ACPI: PCI Interrupt 0000:05:00.1[A] -> GSI 21 (level, low) -> IRQ 22
[   30.689388] bt878_probe: card id=[0x0], Unknown card.
[   30.689390] Exiting..

also this came after i've done this -
modprobe bttv card=72 tuner=44
this i've seen on a forum.

lspci -v
05:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at 30001000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

05:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Flags: medium devsel, IRQ 22
	Memory at 30000000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data
	Capabilities: [4c] Power Management version 2

Can anyone help???
Thanks in advance.

---

### Post by wolfen69 on 2008-06-07
check mythtv's website to make sure it is supported.

---

### Post by Tehriboy on 2008-06-09
I can't find exactly if it is supported or not
but they say that every BT878 card should work, and my falls in the category, so it should work. 
Don't know why it is not working..........

---

