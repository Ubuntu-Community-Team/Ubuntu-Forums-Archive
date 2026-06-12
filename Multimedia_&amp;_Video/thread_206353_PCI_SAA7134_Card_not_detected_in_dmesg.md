---
title: "PCI SAA7134 Card not detected in dmesg"
date: 2006-06-29
forum: Multimedia &amp; Video
---

### Post by naes on 2006-06-29
I sucessfully got my Mercury TV card saa7134 working by blacklisting the saa7134_alsa module and loading saa7134 module.

Since upgrading both motherboard & processor the pci tvcard isn't even detected using lspci. The module gets loaded as indicated in dmesg

```
[17179600.784000] Linux video capture interface: v1.00
[17179600.872000] saa7130/34: v4l2 driver version 0.2.14 loaded

```

however no devices are created. The card itself is still working as I checked it again on the motherboard I upgraded from and all works fine as indicated by lspci 

```
0000:00:0b.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
```

& dmesg

```
[17179597.708000] Linux video capture interface: v1.00
[17179597.796000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179597.796000] **** SET: Misaligned resource pointer: cb1a0c02 Type 07 Len 0
[17179597.796000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179597.796000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179597.796000] saa7130[0]: found at 0000:00:0b.0, rev: 1, irq: 11, latency: 32, mmio: 0xeb800000
[17179597.796000] saa7130[0]: subsystem: 18d0:2100, board: 10MOONS PCI TV CAPTURE CARD [card=21,insmod option]
[17179597.796000] saa7130[0]: board init: gpio is 38500
[17179597.932000] saa7130[0]: i2c eeprom 00: d0 18 00 21 10 28 ff ff ff ff ff ff ff ff ff ff
[17179597.932000] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.932000] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.932000] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.932000] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.932000] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.932000] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.932000] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.992000] tuner 3-0061: chip found @ 0xc2 (saa7130[0])
[17179597.992000] tuner 3-0061: type set to 37 (LG PAL (newer TAPC series))
[17179598.008000] saa7130[0]: registered device video0 [v4l2]
[17179598.008000] saa7130[0]: registered device vbi0
[17179598.008000] saa7130[0]: registered device radio0
```

---

