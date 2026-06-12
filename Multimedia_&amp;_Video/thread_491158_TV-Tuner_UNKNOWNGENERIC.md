---
title: "TV-Tuner UNKNOWN/GENERIC"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by viruzeno on 2007-07-03
Hi, 

i have a asus a7c laptop with a avermedia DVT card, it is showing up incorrectly in the device manager.

here are the results of a dmesg

```
[   18.352915] saa7130/34: v4l2 driver version 0.2.14 loaded
[   18.352974] ACPI: PCI Interrupt 0000:01:02.0[A] -> Link [LNKD] -> GSI 6 (level, low) -> IRQ 6
[   18.352983] saa7133[0]: found at 0000:01:02.0, rev: 209, irq: 6, latency: 64, mmio: 0xf9dff800
[   18.352989] saa7133[0]: subsystem: 1461:4836, board: UNKNOWN/GENERIC [card=0,autodetected]
[   18.352996] saa7133[0]: board init: gpio is 0
[   18.355349] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   18.496492] saa7133[0]: i2c eeprom 00: 61 14 36 48 00 00 00 00 00 00 00 00 00 00 00 00
[   18.496502] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   18.496510] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 80 ff ff ff ff
[   18.496518] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.496526] saa7133[0]: i2c eeprom 40: ff 6b 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[   18.496533] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.496541] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.496549] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   18.496806] saa7133[0]: registered device video0 [v4l2]
[   18.496833] saa7133[0]: registered device vbi0
[   18.517781] saa7134 ALSA driver for DMA sound loaded
[   18.517806] saa7133[0]/alsa: saa7133[0] at 0xf9dff800 irq 6 registered as card -2
```

from what i have read i need to set a card number to make it detect it, however because i also have a ATI x1450 and am forced to run the altered X11 drivers i cannot work out how to install the gatos drivers.

so i have no idea how to get the card number so that i can even attempt to force the kernel to load a module with the correct drivers. 

i have searched the net to the end of my sanity, but i will continue,

can anyone help!!!

---

### Post by fsando on 2007-07-15
I have a laptop asus w1jc. 
I'm trying to solve the same problem. If you find a solution please post it (I will, of course, do the same if I find out).

---

### Post by danap on 2008-01-28
Hello,

I have a laptop Asus A7CC
This tv tunner is a AVerMedia M10D Hybrid DVBT and I don know how configure it.:mad:

---

### Post by marioshrist on 2008-05-14
I also have the same problem. I dont know if the upgrade to hard will fix it

---

