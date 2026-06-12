---
title: "Pinacle PCTV Studio PCI card no longer works"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by Amon_Re on 2008-01-18
My PCTV card apperantly doesn't work anymore ever since i upgraded to Gutsy, i know it worked in Dapper, and i think it worked in Feisty too, but i haven't been needing it much lately, so i'm not sure if it stopped working with Gutsy recently.

my lspci gives me this:

```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82801I (ICH9 Family) Gigabit Ethernet Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
[COLOR="Red"][B]06:00.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
06:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)[/B][/COLOR]
06:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
```

So the card is found on the PCI bridge, dmesg | grep bt878 gives me this:

```
[   38.553882] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   38.653079] bt878: AUDIO driver version 0.0.0 loaded
[   39.150527] bt878: Bt878 AUDIO function found (0).
[   39.150547] bt878_probe: card id=[0x1211bd], Unknown card.
[   39.150555] bt878: [COLOR="Red"]**probe of 0000:06:00.1 failed with error -22**[/COLOR]
```

So it seems Ubuntu (or the linux kernel) has forgotten about this particular piece of kit, question is, how can i resolve it?
Grepping dmesg on bttv gives me:
```
[   38.488011] bttv: driver version 0.9.17 loaded
[   38.488014] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   38.488056] bttv: Bt8xx card found (0).
[   38.488083] bttv0: Bt878 (rev 17) at 0000:06:00.0, irq: 21, latency: 32, mmio: 0x50001000
[   38.488090] bttv0: detected: Pinnacle PCTV [card=39], PCI subsystem ID is 11bd:0012
[   38.488092] bttv0: using: Pinnacle PCTV Studio/Rave [card=39,autodetected]
[   38.488113] bttv0: gpio: en=00000000, out=00000000 in=00ff67ff [init]
[   38.488457] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   38.489160] bttv0: miro: id=25 tuner=1 radio=no stereo=no
[   38.489162] bttv0: using tuner=1
[   38.489163] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   38.489759] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   38.490356] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   38.490955] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   38.587341] bttv0: registered device video1
[   38.587364] bttv0: registered device vbi0
[   38.587387] bttv0: PLL: 28636363 => 35468950 .. ok
```

Anyone have any experiance with these things?

---

