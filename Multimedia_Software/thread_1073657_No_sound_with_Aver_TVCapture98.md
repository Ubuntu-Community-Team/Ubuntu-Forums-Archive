---
title: "No sound with Aver TVCapture98"
date: 2009-02-18
forum: Multimedia Software
---

### Post by bgenc on 2009-02-18
Hi,

I have this maybe 10 years old video capture card AverMedia TVCapture98. I have been using this card in windows with no problems since day 1. But with linux it has never worked.

Since I switched from Windows to Ubuntu, I had no regrets but this. Whatever I did, I couldn't make this card work perfectly. By perfectly, I mean this: I can watch tv using tvtime, but I can't hear any sound. I tried almost every thing and read numerous things on the web. Most of the stuff on the web are outdated and doesn't directly work in Intrepid. And I am not a linux guru myself to improvise solutions. 

Here is my lspci: 

```

01:08.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:08.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

Here is dmesg:

```

[   17.238493] Linux video capture interface: v2.00
[   17.315726] bttv: driver version 0.9.17 loaded
[   17.315730] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   17.316219] Registered led device: rt2500pci-phy0:radio
[   17.316610] bttv: Bt8xx card found (0).
[   17.316626] bttv 0000:01:08.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   17.316634] bttv0: Bt878 (rev 17) at 0000:01:08.0, irq: 18, latency: 32, mmio: 0xfdeff000
[   17.316645] bttv0: detected: AVerMedia TVCapture 98 [card=13], PCI subsystem ID is 1461:0004
[   17.316648] bttv0: using: AVerMedia TVCapture 98 [card=13,autodetected]
[   17.316681] bttv0: gpio: en=00000000, out=00000000 in=00867ff3 [init]
[   17.319163] bttv0: Hauppauge/Voodoo msp34xx: reset line init [11]
[   17.345436] bttv0: Avermedia eeprom[0x4011]: tuner=5 radio:no remote control:yes
[   17.345441] bttv0: tuner type=5
[   17.345444] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   17.348082] bttv0: i2c: checking for MSP34xx (alternate address) @ 0x88... not found
[   17.348572] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   17.349061] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   17.392868] tuner' 2-0061: chip found @ 0xc2 (bt878 #0 [sw])
[   17.441989] tuner-simple 2-0061: creating new instance
[   17.441993] tuner-simple 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   17.449549] bttv0: registered device video0
[   17.449580] bttv0: registered device vbi0
[   17.449597] bttv0: PLL: 28636363 => 35468950 .. ok
[   17.480647] input: bttv IR (card=13) as /devices/pci0000:00/0000:00:09.0/0000:01:08.0/input/input7

```

and lsmod | grep bttv

```

bttv                  171028  0 
videodev               41344  2 tuner,bttv
ir_common              48900  1 bttv
compat_ioctl32          9344  1 bttv
i2c_algo_bit           14340  1 bttv
v4l2_common            19840  3 tuner,tvaudio,bttv
videobuf_dma_sg        20612  1 bttv
videobuf_core          26628  2 bttv,videobuf_dma_sg
btcx_risc              12552  1 bttv
tveeprom               20228  1 bttv
i2c_core               31892  9 tuner_simple,tuner,tvaudio,bttv,i2c_algo_bit,nvidia,v4l2_common,tveeprom,i2c_nforce2

```

If you guys can help me get sound out of this card, I will really appreciate it.

---

### Post by bgenc on 2009-02-19
Is there a more suitable forum where I can get an answer to this problem? Could you guys at least forward me to somewhere else?

---

