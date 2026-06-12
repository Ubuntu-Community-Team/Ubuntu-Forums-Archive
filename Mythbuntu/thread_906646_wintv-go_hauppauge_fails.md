---
title: "wintv-go hauppauge fails"
date: 2008-08-31
forum: Mythbuntu
---

### Post by mwcrowley on 2008-08-31
The card is recognized I set it up in MythTv with a Hauppauge 150.  The hauppauge150 works perfectly, recording and playing tv.  The wintv-go gives me static or a green screen, and when I set up two shows to record at once, it also fails.  Also when I scan for channels in MythTV Backend Setup, setup crashes.  

Here's my output from dmesg:
```
  20.519351] bttv: Bt8xx card found (0).
[   20.519375] bttv 0000:01:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, high) -> IRQ 17
[   20.519386] bttv0: Bt878 (rev 17) at 0000:01:09.0, irq: 17, latency: 32, mmio: 0xe4000000
[   20.519403] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[   20.519406] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[   20.519441] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[   20.521932] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[   20.525296] tuner' 3-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   20.562554] tveeprom 3-0050: Hauppauge model 44811, rev D123, serial# 6250648
[   20.562558] tveeprom 3-0050: tuner model is Philips FM1236 (idx 23, type 2)
[   20.562561] tveeprom 3-0050: TV standards NTSC(M) (eeprom 0x08)
[   20.562563] tveeprom 3-0050: audio processor is None (idx 0)
[   20.562566] tveeprom 3-0050: has radio
[   20.562568] bttv0: Hauppauge eeprom indicates model#44811
[   20.562571] bttv0: tuner type=2
[   20.582247] tuner-simple 3-0061: creating new instance
[   20.582252] tuner-simple 3-0061: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   20.582806] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   20.583339] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   20.583866] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   20.644947] bttv0: registered device video1
[   20.644993] bttv0: registered device vbi1
[   20.645035] bttv0: registered device radio0
[   20.645065] bttv0: PLL: 28636363 => 35468950 .. ok
[   20.676624] ivtv:  End initialization

```


and from lspci -v
```
01:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. Device 13eb
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at e4000000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: bttv
	Kernel modules: bttv

01:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
	Subsystem: Hauppauge computer works Inc. Device 13eb
	Flags: bus master, medium devsel, latency 32, IRQ 17
	Memory at e4001000 (32-bit, prefetchable) [size=4K]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: Bt87x
	Kernel modules: snd-bt87x

```

---

### Post by DemonBob on 2008-08-31
Try this in a terminal

sudo modprobe bttv card=10 tuner=2 

Then try to watch tv again.

---

### Post by mwcrowley on 2008-08-31
Thanks for the reply.  But no go.  Screen is just green.

---

### Post by mwcrowley on 2008-09-02
Is there anyone who knows how to get these cards working?  If you have one can you give me your config?

---

