---
title: "Twinhan Ter-CI problem"
date: 2007-05-26
forum: Multimedia &amp; Video
---

### Post by _pitch on 2007-05-26
Hi,

First I just have to thank all of you who have contributed to this forum and the rest of the open source community.

My problem is my new mobo.
I've bought a ASUS P5B-V, with a Intel Core2Duo 2.4GHz and thought that my Twinhan Ter-CI card should work with it. Did not!!!
The dmesg is :
```
[ 1488.446138] Linux video capture interface: v2.00
[ 1488.454309] i2c-core: driver [tveeprom] registered
[ 1488.546036] bttv: driver version 0.9.17 loaded
[ 1488.546114] bttv: using 8 buffers with 2080k (520 pages) each for capture
[ 1488.546263] bttv: Bt8xx card found (0).
[ 1488.546337] ACPI: PCI Interrupt 0000:04:01.0[A] -> GSI 22 (level, low) -> IRQ 22
[ 1488.546445] bttv0: Bt878 (rev 17) at 0000:04:01.0, irq: 22, latency: 32, mmio: 0xbfefe000
[ 1488.546561] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
[ 1488.546671] bttv0: using: Twinhan DST + clones [card=113,insmod option]
[ 1488.546768] bttv0: gpio: en=00000000, out=00000000 in=00f500fd [init]
[ 1488.546870] PM: Adding info for No Bus:i2c-0
[ 1488.546952] i2c_adapter i2c-0: adapter [bt878 #0 [hw]] registered
[ 1488.547036] bttv0: using tuner=4
[ 1488.579723] i2c-core: driver [tuner] registered
[ 1488.579894] PM: Adding info for bttv-sub:dvb0
[ 1488.579913] bttv0: add subdevice "dvb0"
[ 1488.591571] bt878: AUDIO driver version 0.0.0 loaded
[ 1488.591737] bt878: Bt878 AUDIO function found (0).
[ 1488.591819] ACPI: PCI Interrupt 0000:04:01.1[A] -> GSI 22 (level, low) -> IRQ 22
[ 1488.591918] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
[ 1488.592041] bt878(0): Bt878 (rev 17) at 04:01.1, irq: 22, latency: 32, memory: 0xbfeff000
[ 1558.761133] DVB: registering new adapter (bttv0).
[ 1559.041109] i2c_adapter i2c-0: master_xfer[0] W, addr=0x55, len=8
[ 1559.066066] i2c_adapter i2c-0: master_xfer[0] W, addr=0x55, len=8
[ 1559.116984] dst(0) dst_probe: unknown device.
[ 1559.117042] frontend_init: Could not find a Twinhan DST.
[ 1559.117051] dvb-bt8xx: A frontend driver was not found for device 109e/0878 subsystem 1822/0001
```

The card worked earlier on a PIII with a slack dist and I've have had this problem earlier but that was solved by power down for about 5 minutes and option pci=noacpi and pci=routeirq on lilo. This "work around" doesn't work on my new putar.

How do I solve the problem?
I appreciate  all answers.

/_pitch

---

### Post by _pitch on 2007-05-31
Bump...

---

