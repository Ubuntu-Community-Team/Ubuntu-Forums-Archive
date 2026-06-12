---
title: "How do I get Avermedia M103 to work?"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by Chongo on 2008-01-10
I think that I have the Avermedia M103 mini PCI card in my laptop.

I am running Kubuntu 7.10, The Gutsy Gibbon.

I believe that this card has the following chips:

XC3028

MT352

SAA7135

lspci -v gives:

05:07.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broa
dcast Decoder (rev d1)
        Subsystem: Avermedia Technologies Inc Unknown device f736
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at b0106000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

lspci -nv gives:

05:07.0 0480: 1131:7133 (rev d1)
        Subsystem: 1461:f736
        Flags: bus master, medium devsel, latency 64, IRQ 23
        Memory at b0106000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

dmesg gives:

[   15.680000] saa7130/34: v4l2 driver version 0.2.14 loaded
[   15.680000] ACPI: PCI Interrupt 0000:05:07.0[A] -> Link [LNK4] -> GSI 19 (level, low) -> IRQ 23
[   15.680000] saa7133[0]: found at 0000:05:07.0, rev: 209, irq: 23, latency: 64, mmio: 0xb0106000
[   15.680000] saa7133[0]: subsystem: 1461:f736, board: UNKNOWN/GENERIC [card=0,autodetected]
[   15.680000] saa7133[0]: board init: gpio is 220000
[   15.816000] saa7133[0]: i2c eeprom 00: 61 14 36 f7 00 00 00 00 00 00 00 00 00 00 00 00
[   15.816000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   15.816000] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 01 01 03 08 ff 00 0f ff ff ff ff
[   15.816000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.816000] saa7133[0]: i2c eeprom 40: ff 65 00 ff c2 1e ff ff ff ff ff ff ff ff ff ff
[   15.816000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.816000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.816000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   15.816000] saa7133[0]: registered device video1 [v4l2]
[   15.816000] saa7133[0]: registered device vbi0
[   15.876000] saa7134 ALSA driver for DMA sound loaded
[   15.876000] saa7133[0]/alsa: saa7133[0] at 0xb0106000 irq 23 registered as card -2

I've tried: sudo modprobe saa7134 saa7134-dvb saa7134-alsa, and also looking on the web there appears to be reference to xc3028-tuner, but modprobe can't find that.

Any help would be hugely appreciated.

Many thanks,

Tom

:-({|=

---

### Post by Chongo on 2008-01-10
Oops, didn't really say what I wanted to achieve!

The card doesn't seem to work at the moment, maybe I need to select a particular card number or get a more up to date driver?

I'd just like to be able to use the DVB part of the card in Kaffeine.

:popcorn:

---

### Post by jonface on 2008-01-19
I'd also be interested.

Laptop is a Clevo D900K.

---

### Post by RobPotts on 2008-02-20
Hi,
Have you had any luck getting this card to work?  I'm also trying to find a solution, it looks the similar to the A16D E506, which has experiamntlal code at [http://mcentral.de](http://mcentral.de), but I cannot get it to work yet.

Rob

---

### Post by jonface on 2008-05-04
*bump*

Anyone?

I guess I'm going to have to open my laptop up and see what it says on the chips. Damn these crazy devices.

---

