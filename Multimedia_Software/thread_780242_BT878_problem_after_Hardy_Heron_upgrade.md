---
title: "BT878 problem after Hardy Heron upgrade"
date: 2008-05-03
forum: Multimedia Software
---

### Post by groesbeck on 2008-05-03
I have two bt878 video capture cards.  They worked fine since RH9 and through Feisty and Gutsy.  I upgraded to Hardy and I can't get them to work at all.

I've never had to edit any of the modprobe.d files to get these to work.

I don't know if it's a bttv driver problem or a kernel module change that's broken things.  I've been googling for a couple days with no success.

Here is the relevant dmesg output

54.640247] bttv: driver version 0.9.16 loaded
[   54.640253] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   54.640335] bttv: Bt8xx card found (0).
[   54.640372] ACPI: PCI Interrupt 0000:00:0f.0[A] -> GSI 18 (level, low) -> IRQ 22
[   54.640389] bttv0: Bt878 (rev 17) at 0000:00:0f.0, irq: 22, latency: 32, mmio: 0xee000000
[   54.640403] bttv0: detected: Provideo PV143A [card=105], PCI subsystem ID is aa00:1430
[   54.640407] bttv0: using: ProVideo PV143 [card=105,autodetected]
[   54.640442] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   54.640951] bttv0: using tuner=-1
[   54.640955] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   54.641765] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   54.642574] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   54.643434] bttv0: registered device video0
[   54.643469] bttv0: registered device vbi0
[   54.643489] bttv0: PLL: 28636363 => 35468950 .. ok
[   54.674722] bttv: Bt8xx card found (1).
[   54.674753] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 19 (level, low) -> IRQ 19
[   54.674769] bttv1: Bt878 (rev 17) at 0000:00:10.0, irq: 19, latency: 32, mmio: 0xed000000
[   54.674799] bttv1: detected: Prolink Pixelview PV-BT [card=72], PCI subsystem ID is 1554:4011
[   54.674804] bttv1: using: Prolink Pixelview PV-BT878P+9B (PlayTV Pro rev.9B FM+NICAM) [card=72,autodetected]
[   54.674835] bttv1: gpio: en=00000000, out=00000000 in=006fc0ff [init]
[   54.675396] bttv1: using tuner=5
[   54.675401] bttv1: i2c: checking for TDA7432 @ 0x8a... not found
[   54.695124] parport: PnPBIOS parport detected.
[   54.695183] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   54.713867] input: ImExPS/2 Generic Explorer Mouse as /class/input/input3
[   54.753601] bttv1: i2c: checking for TDA9887 @ 0x86... not found
[   54.793179] tuner 2-0061: chip found @ 0xc2 (bt878 #1 [sw])
[   54.793220] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   54.793224] tuner 2-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   54.794219] tuner 2-0063: chip found @ 0xc6 (bt878 #1 [sw])
[   54.804244] bttv1: registered device video1
[   54.804280] bttv1: registered device vbi1
[   54.804315] bttv1: registered device radio0
[   54.804338] bttv1: PLL: 28636363 => 35468950 .. ok
[   54.835540] input: bttv IR (card=72) as /class/input/input4
[   54.937052] bt878: AUDIO driver version 0.0.0 loaded
[   54.937111] bt878: Bt878 AUDIO function found (0).
[   54.937137] ACPI: PCI Interrupt 0000:00:0f.1[A] -> GSI 18 (level, low) -> IRQ 22
[   54.937147] bt878_probe: card id=[0x1430aa00], Unknown card.
[   54.937148] Exiting..
[   54.937154] ACPI: PCI interrupt for device 0000:00:0f.1 disabled
[   54.937160] bt878: probe of 0000:00:0f.1 failed with error -22
[   54.937168] bt878: Bt878 AUDIO function found (0).
[   54.937185] ACPI: PCI Interrupt 0000:00:10.1[A] -> GSI 19 (level, low) -> IRQ 19
[   54.937192] bt878_probe: card id=[0x40111554], Unknown card.
[   54.937194] Exiting..
[   54.937199] ACPI: PCI interrupt for device 0000:00:10.1 disabled
[   54.937203] bt878: probe of 0000:00:10.1 failed with error -22

---

### Post by mwcrowley on 2008-05-14
I have a wintv card bt878 chipset, that works with tvtime.  The only sound I get is from the lineout jack.  I could never use it with mythtv because there was never a sound capture.  
Did you have sound working on yours?

---

### Post by groesbeck on 2008-05-15
> **mwcrowley said:**
> I have a wintv card bt878 chipset, that works with tvtime.  The only sound I get is from the lineout jack.  I could never use it with mythtv because there was never a sound capture.  
Did you have sound working on yours?

I've never tried to use sound.  I only capture video from my security cameras.

---

