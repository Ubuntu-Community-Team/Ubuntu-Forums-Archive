---
title: "MythBuntu 10.10: Hauppage WinTV (bt878) no longer supported"
date: 2010-10-17
forum: Mythbuntu
---

### Post by StijnS on 2010-10-17
Last week I installed the latest MythBuntu 10.10 release on a computer I intend to use as a mediacenter. The specs: Fujitsu-Siemens Scenic-D, Pentium 4 2.4GHz, 256MB ram, Nvidia FX5200, Hauppage WinTV (bt878) TV card.
The problem is that this TV card no longer works in this release, although it worked fine in MythBuntu 9.04. I tried some things to get it to work on 10.10:
```

stijn@mythTV:~$ dmesg | egrep '(bttv|bt87?|tveeprom)'
[    5.951701] bttv: driver version 0.9.18 loaded
[    5.951707] bttv: using 8 buffers with 2080k (520 pages) each for capture
[    5.952980] bttv: Bt8xx card found (0).
[    5.953011] bttv 0000:02:07.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.953027] bttv0: Bt878 (rev 17) at 0000:02:07.0, irq: 18, latency: 132, mmio: 0xc0500000
[    5.953071] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[    5.953076] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[    5.953121] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[    5.955602] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[    5.986340] tveeprom 0-0050: Hauppauge model 44004, rev C108, serial# 2271273
[    5.986346] tveeprom 0-0050: tuner model is Philips FI1216 MK2 (idx 8, type 5)
[    5.986350] tveeprom 0-0050: TV standards PAL(B/G) (eeprom 0x04)
[    5.986354] tveeprom 0-0050: audio processor is None (idx 0)
[    5.986357] tveeprom 0-0050: has no radio
[    5.986360] bttv0: Hauppauge eeprom indicates model#44004
[    5.986364] bttv0: tuner type=5
[    6.741890] bttv0: audio absent, no audio device found!
[    7.121831] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[    7.968586] bttv0: registered device video0
[    7.968755] bttv0: registered device vbi0
[    7.968779] bttv0: PLL: 28636363 => 35468950 .. ok
[    8.005120] bt87x0: Using board 1, analog, digital (rate 32000 Hz)
[  305.876086] bttv0: PLL can sleep, using XTAL (28636363).
```But when opening xawtv, it gave some errors:
```

stijn@mythTV:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.35-22-generic)
xinerama 0: 1440x900+0+0
WARNING: couldn't find framebuffer base address, try manual
         configuration ("v4l-conf -a <addr>")
v4l2: WARNING: framebuffer base address mismatch
v4l2: me=(nil) v4l=(nil)
Warning: Cannot convert string "-*-ledfixed-medium-r-*--39-*-*-*-c-*-*-*" to type FontStruct

game over

```But after entering these commands:
```
[FONT=monospace]
[/FONT]sudo v4l-conf -a 0xF0000000[FONT=monospace]
[/FONT]v4l-conf -1[FONT=Verdana]
[/FONT]
```[FONT=Verdana]
I got xawtv to work, but only when I set capture to grabdisplay.
But still MythTV doesn't find any TV channels. Does anyone have any suggestions?

Thanks,

Stijj
[/FONT]

---

