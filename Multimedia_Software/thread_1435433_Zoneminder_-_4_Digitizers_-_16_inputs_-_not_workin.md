---
title: "Zoneminder - 4 Digitizers - 16 inputs - not working"
date: 2010-03-21
forum: Multimedia Software
---

### Post by ajroach42 on 2010-03-21
I've installed Zoneminder 


Relevent Info from lspci
```
02:04.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:04.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:05.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:05.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:06.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:06.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:07.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:07.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```[]

From dmesg 
```
[   16.854327] bttv0: registered device video0
[   16.854365] bttv0: registered device vbi0
[   16.854411] bttv: Bt8xx card found (1).
[   16.854439] bttv 0000:02:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   16.854453] bttv1: Bt878 (rev 17) at 0000:02:05.0, irq: 21, latency: 32, mmio: 0xf8102000
[   16.854598] bttv1: subsystem: 8251:55aa (UNKNOWN)
[   16.854600] please mail id, board name and the correct card= insmod option to linux-media@vger.kernel.org
[   16.854604] bttv1: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   16.854608] IRQ 21/bttv1: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.854644] bttv1: gpio: en=00000000, out=00000000 in=00ffff1f [init]
[   16.885482] bttv1: tuner type unset
[   16.888191] bttv1: registered device video1
[   16.888221] bttv1: registered device vbi1
[   16.888268] bttv: Bt8xx card found (2).
[   16.888294] bttv 0000:02:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   16.888308] bttv2: Bt878 (rev 17) at 0000:02:06.0, irq: 22, latency: 32, mmio: 0xf8104000
[   16.888487] bttv2: subsystem: 8252:55aa (UNKNOWN)
[   16.888490] please mail id, board name and the correct card= insmod option to linux-media@vger.kernel.org
[   16.888494] bttv2: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   16.888497] IRQ 22/bttv2: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.888532] bttv2: gpio: en=00000000, out=00000000 in=00ffff1f [init]
[   16.918967] bttv2: tuner type unset
[   16.921278] bttv2: registered device video2
[   16.921306] bttv2: registered device vbi2
[   16.921348] bttv: Bt8xx card found (3).
[   16.921372]   alloc irq_desc for 23 on node -1
[   16.921375]   alloc kstat_irqs on node -1
[   16.921385] bttv 0000:02:07.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   16.921399] bttv3: Bt878 (rev 17) at 0000:02:07.0, irq: 23, latency: 32, mmio: 0xf8106000
[   16.921567] bttv3: subsystem: 8253:55aa (UNKNOWN)
[   16.921570] please mail id, board name and the correct card= insmod option to linux-media@vger.kernel.org
[   16.921574] bttv3: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   16.921577] IRQ 23/bttv3: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.921676] bttv3: gpio: en=00000000, out=00000000 in=00ffff1b [init]
[   16.952293] bttv3: tuner type unset
[   16.952945] bttv3: registered device video3
[   16.952972] bttv3: registered device vbi3
```


Under windows I had this card managing 13 cameras. It can manage up to 16. I'm assuming that the card has 4 multiplexed digitizers which can support 4 inputs each. Right now using zoneminder I can only get video feed off of 4 cameras (1 per digitizer, no multiplexing.) 

My CCTV machine for the store I operate crashed. The software that I was using under windows is no longer supported or updated, and I'm not really sure what it was. I migrated this system to linux, which I had been planning on doing for quite some time. 

Sadly, 4 video feeds. I need all 13 working, although 3-5 Frames per second is more than sufficient. 


Please help! 

Thank you,


Andrew

---

### Post by nickmcg on 2011-10-03
Hi, did you manage to resolve this?

I have a similar issue, but it seems to involve a USB dongle too :(

---

### Post by marguin on 2011-10-22
anyone find resolution to this?  i am having the same problem... pci card, 16 inputs over /dev/video[0-3]

---

