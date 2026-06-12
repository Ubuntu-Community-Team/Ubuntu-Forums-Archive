---
title: "Install problems Compro VideoMate DVB-T300"
date: 2006-04-17
forum: Multimedia &amp; Video
---

### Post by J0ris on 2006-04-17
Hi people,

There is something seriously weird going on on this machine. I'm trying to install the above-mentioned card in Dapper Drake Flight 6. The following is the output from dmesg:

[   46.773475] saa7130/34: v4l2 driver version 0.2.14 loaded
[   46.888089] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 17
[   46.888095] GSI 22 sharing vector 0x42 and IRQ 22
[   46.888102] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [LNKA] -> GSI 17 (level, low) -> IRQ 66
[   46.888110] saa7134[0]: found at 0000:04:08.0, rev: 1, irq: 66, latency: 64, mmio: 0xfaaff400
[   46.888116] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,autodetected]
[   46.888128] saa7134[0]: board init: gpio is 843f00
[   46.888195] input: saa7134 IR (Compro Videomate DV as /class/input/input2
[   47.011466] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   47.011474] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   47.011481] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[   47.011487] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   47.011494] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   47.011500] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   47.011506] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   47.011513] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   47.043425] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[   47.046421] tuner 0-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   47.046424] tuner 0-0061: type set to 67 (Philips TD1316 Hybrid Tuner)
[   47.049421] tuner 0-0068: chip found @ 0xd0 (saa7134[0])
[   47.059409] tda9887 0-0043: chip found @ 0x86 (saa7134[0])
[   47.062768] saa7134[0]: registered device video0 [v4l2]
[   47.062789] saa7134[0]: registered device vbi0
[   47.071009] saa7134 ALSA driver for DMA sound loaded
[   47.071034] saa7134[0]/alsa: saa7134[0] at 0xfaaff400 irq 66 registered as card -1

As far as I can see this is pretty much what it is supposed to look like (at least as far as correct hardware detection goes, I don't know about the rest).
Then I installed Xawtv with Synaptic Package Manager and tried to run it from command line. This is what it said:

joris@Serendipity:~$ xawtv
This is xawtv-3.94, running on Linux/x86_64 (2.6.15-20-amd64-generic)
Warning: locale not supported by Xlib, locale set to C
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65

When I ran dmesg again the following was the output:

[   38.607424] ACPI: PCI Interrupt 0000:04:08.0[A] -> Link [LNKA] -> GSI 17 (level, low) -> IRQ 66
[   38.607432] saa7134[0]: found at 0000:04:08.0, rev: 1, irq: 66, latency: 64, mmio: 0xfaaff400
[   38.607438] saa7134[0]: subsystem: 1850:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   38.607450] saa7134[0]: board init: gpio is 843f00
[   38.730107] saa7134[0]: i2c eeprom 00: 02 10 00 01 04 00 1c 00 40 03 00 10 04 00 82 10
[   38.730115] saa7134[0]: i2c eeprom 10: 00 e7 02 00 01 00 10 26 52 41 c0 06 f8 ed cb 00
[   38.730121] saa7134[0]: i2c eeprom 20: 00 40 01 02 03 41 00 01 00 5e 00 06 40 e7 32 00
[   38.730127] saa7134[0]: i2c eeprom 30: 01 5f 20 77 ac 5e 00 88 53 71 32 8c c0 01 0f 50
[   38.730134] saa7134[0]: i2c eeprom 40: 26 02 00 00 02 00 67 00 00 50 51 2b 02 24 66 2b
[   38.730140] saa7134[0]: i2c eeprom 50: 00 24 67 50 70 e7 66 00 01 71 66 cc 03 50 26 0b
[   38.730146] saa7134[0]: i2c eeprom 60: 00 24 66 71 57 96 bc 9b 7f 38 57 05 0f 73 58 a0
[   38.730152] saa7134[0]: i2c eeprom 70: 57 38 57 7c 58 4e 9f 83 f2 ff 80 30 58 d5 b8 14
[   38.730282] saa7134[0]: registered device video0 [v4l2]
[   38.730374] saa7134[0]: registered device vbi0
[   38.738692] saa7134 ALSA driver for DMA sound loaded
[   38.738717] saa7134[0]/alsa: saa7134[0] at 0xfaaff400 irq 66 registered as card -1

This remained the same after removing xawtv with synaptic package manager. Does anybody know what is going on? Since I'm new with linux I'm not sure what the appropriate next step ought to be. Thanks!

---

