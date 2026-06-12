---
title: "Hauppauge WinTV-HVR1270 Stopped Working (8.10)"
date: 2009-11-09
forum: Mythbuntu
---

### Post by gatecrasher on 2009-11-09
I am running Intrepid, and I had this working not too long ago, then I noticed that I was missing recordings. Once I checked, I realized that mythtv was no longer seeing the card. The dmesg output is below. I've already recompiled the v4l drivers multiple times with a couple of different kernels. I also have the firmware in place. Any seen this before?

Linux myth 2.6.27-15-generic #1 SMP Tue Oct 20 06:52:09 UTC 2009 i686 GNU/Linux


```
[   13.310376] cx23885 driver version 0.0.2 loaded
[   16.708195] cx23885 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   16.708257] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1270 [card=18,autodetected]
[   16.854527] cx23885[0]: hauppauge eeprom: model=22111
[   16.854529] cx23885_dvb_register() allocating 1 frontend(s)
[   16.855272] cx23885[0]: cx23885 based dvb card
[   16.903313] cx23885[0]: frontend initialization failed
[   16.903316] cx23885_dvb_register() dvb_register failed err = -1
[   16.903318] cx23885_dev_setup() Failed to register dvb on VID_C
[   16.903322] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   16.903330] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfd400000
[   16.903339] cx23885 0000:03:00.0: setting latency timer to 64

```

---

### Post by gatecrasher on 2009-11-11
Weird. I powered off the machine and now the card shows up again. I'm starting to suspect that the card is faulty. I re-installed the drivers and rebooted about 20 times. One thing I did not do was power the machine off. Perhaps something was never flushed/drained until I powered it off. Who knows. 

Linux myth 2.6.27-15-generic #1 SMP Tue Oct 20 06:52:09 UTC 2009 i686 GNU/Linux


```
[   14.104996] cx23885 driver version 0.0.2 loaded
[   14.804550] cx23885 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.804600] CORE cx23885[0]: subsystem: 0070:2211, board: Hauppauge WinTV-HVR1270 [card=18,autodetected]
[   14.950633] cx23885[0]: hauppauge eeprom: model=22111
[   14.950636] cx23885_dvb_register() allocating 1 frontend(s)
[   14.950650] cx23885[0]: cx23885 based dvb card
[   15.328684] DVB: registering new adapter (cx23885[0])
[   15.328976] cx23885_dev_checkrevision() Hardware revision = 0xd0
[   15.328985] cx23885[0]/0: found at 0000:03:00.0, rev: 4, irq: 18, latency: 0, mmio: 0xfd400000
[   15.328992] cx23885 0000:03:00.0: setting latency timer to 64

```

---

