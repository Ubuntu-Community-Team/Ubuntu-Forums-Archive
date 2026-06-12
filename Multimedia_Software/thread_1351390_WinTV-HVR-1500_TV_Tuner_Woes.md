---
title: "WinTV-HVR-1500 TV Tuner Woes"
date: 2009-12-10
forum: Multimedia Software
---

### Post by markackerman8@gmail.com on 2009-12-10
WinTV-HVR-1500 is driving me crazy .... any help would be greatly appreciated so I dont go back to windows ARGHHHH
nothing I do can seem to get my tuner card to show anything

here's my dmesg

cx23885 driver version 0.0.2 loaded
[    8.602182] cx23885 0000:04:00.0: enabling device (0000 -> 0002)
[    8.602191] cx23885 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.602315] CORE cx23885[0]: subsystem: 0070:7797, board: Hauppauge WinTV-HVR1500Q [card=5,autodetected]
[    8.732278] tveeprom 0-0050: Hauppauge model 77041, rev E2F0, serial# 3746385
[    8.732282] tveeprom 0-0050: MAC address is 00-0D-FE-39-2A-51
[    8.732285] tveeprom 0-0050: tuner model is Xceive XC5000 (idx 150, type 76)
[    8.732288] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[    8.732291] tveeprom 0-0050: audio processor is CX23885 (idx 39)
[    8.732293] tveeprom 0-0050: decoder processor is CX23885 (idx 33)
[    8.732295] tveeprom 0-0050: has no radio
[    8.732297] cx23885[0]: hauppauge eeprom: model=77041
[    8.732300] cx23885_dvb_register() allocating 1 frontend(s)
[    8.733646] cx23885[0]: cx23885 based dvb card
[    8.767783] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
......
......
[    8.897116] iwlagn 0000:02:00.0: irq 30 for MSI/MSI-X
[    8.925521] xc5000 1-0061: creating new instance
[    8.926237] xc5000: Successfully identified at address 0x61
[    8.926239] xc5000: Firmware has not been loaded previously
[    8.926243] DVB: registering new adapter (cx23885[0])
[    8.926247] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[    8.926528] cx23885_dev_checkrevision() Hardware revision = 0xb0
[    8.926539] cx23885[0]/0: found at 0000:04:00.0, rev: 2, irq: 17, latency: 0, mmio: 0xf6000000
[    8.926550] cx23885 0000:04:00.0: setting latency timer to 64
[    8.926556] IRQ 17/cx23885[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.244905]   alloc irq_desc for 22 on node 0
[    9.244908]   alloc kstat_irqs on node 0
[    9.244917] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.244977] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.383292] phy0: Selected rate control algorithm 'iwl-agn-rs'



HELPPPP

---

### Post by laceration on 2009-12-10
Here is info on it at Linuxtv.org:
[http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1500](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1500)

It doesn't look like this device is supported out of the box, though you can make it work by patching the driver and recompiling it.  This is beyond what most users want to hassle with.  In other words, support for the WinTV-HVR-1500 isn't too good.  This info does seem kind of old and support for TV devices is constantly being added to newer Linux kernels so it may be worth a google to try and find some info, but I'd say that's a longshot.

Getting TV to work can be difficult in Linux.  I succeeded, but had an easier time of it when I did it in Windows.  I stuck it out because I did not want to go back to Windows!  Your might consider getting a new, better supported, tuner.

---

