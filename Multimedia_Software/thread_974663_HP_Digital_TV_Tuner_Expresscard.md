---
title: "HP Digital TV Tuner Expresscard"
date: 2008-11-07
forum: Multimedia Software
---

### Post by phin on 2008-11-07
Trying to get this card working with ubuntu but can't seem to get it to change channels.

here is my dmesg output;

[   17.330703] cx23885 driver version 0.0.1 loaded
[   17.330768] cx23885 0000:0c:00.0: enabling device (0000 -> 0002)
[   17.330780] cx23885 0000:0c:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   17.330874] CORE cx23885[0]: subsystem: 0070:7797, board: Hauppauge WinTV-HVR1500Q [card=5,autodetected]
[   17.854141] cx23885[0]: i2c bus 0 registered
[   17.854213] cx23885[0]: i2c bus 1 registered
[   17.854260] cx23885[0]: i2c bus 2 registered
[   17.883713] cx23885[0]: hauppauge eeprom: model=77041
[   17.883717] cx23885[0]: cx23885 based dvb card
[   18.547121] DVB: registering new adapter (cx23885[0])
[   18.547801] cx23885_dev_checkrevision() Hardware revision = 0xb0
[   18.547813] cx23885[0]/0: found at 0000:0c:00.0, rev: 2, irq: 19, latency: 0, mmio: 0xdfc00000
[   18.547827] cx23885 0000:0c:00.0: setting latency timer to 64

and;
[   18.547108] xc5000: Successfully identified at address 0x61
[   18.547113] xc5000: Firmware has not been loaded previously

upon opening Me-TV and trying to channels i get Failed to tune to transponder at XXXXXXXXX

the firmware, dvb-fe-xc5000-1.1.fw DOES load, so im not sure what else to do or where to go from here.

thanks in advance.

---

### Post by phin on 2008-11-07
please note, that over the air digital is not as important to me as receiving the analog cable tv input that i have applied to my tuner.

thanks.

---

### Post by phin on 2008-11-09
Ok, ive read that part of my issue is that /dev/video0 is not being created since there is some sort of read-only error going on in /dev/.static/dev

---

### Post by phin on 2008-11-10
bump?

---

