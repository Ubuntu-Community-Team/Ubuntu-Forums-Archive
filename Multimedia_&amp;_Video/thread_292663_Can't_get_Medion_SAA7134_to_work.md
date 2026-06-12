---
title: "Can't get Medion SAA7134 to work"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by Winger on 2006-11-04
Hi there,
I'm using a Medion MD8386XL PC with Edgy Eft. The TV-Card is a Medion SAA7134 (same as Creatix) DVB-T/DVB-S Hybrid card (CTX925) with a Philips FMD1216ME Tuner.

After looking into various threads I think the card should work as card=12 and Tuner=63.

However, after rmmodSAA7134 and morprobe SAA7134 card=12 Tuner=63  I get the following output from demsg:
```

	

[17180961.460000] saa7134[0]: found at 0000:03:01.0, rev: 1, irq: 225, latency: 32, mmio: 0xd8000000
[17180961.460000] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,insmod option]
[17180961.460000] saa7134[0]: board init: gpio is 0
[17180961.620000] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[17180961.636000] tuner 0-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[17180961.644000] tda9887 0-0043: chip found @ 0x86 (saa7134[0])
[17180961.684000] saa7134[0]: i2c eeprom 00: be 16 03 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17180961.684000] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[17180961.684000] saa7134[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 1f 02 51 96 2b
[17180961.684000] saa7134[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[17180961.684000] saa7134[0]: i2c eeprom 40: ff 1d 00 c2 86 10 01 01 00 00 fd 79 44 9f c2 8f
[17180961.684000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff 06 06 0f 00 0f 00 0f 00 0f 00
[17180961.684000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180961.684000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180961.708000] saa7134[0] Board has DVB-T
[17180961.708000] saa7134[0] Tuner type is 63
[17180961.760000] saa7134[0]: registered device video0 [v4l2]
[17180961.760000] saa7134[0]: registered device vbi0
[17180961.760000] saa7134[0]: registered device radio0
[17180961.760000] ACPI: PCI Interrupt 0000:03:04.0[A] -> GSI 20 (level, low) -> IRQ 233
[17180961.760000] saa7134[1]: found at 0000:03:04.0, rev: 1, irq: 233, latency: 32, mmio: 0xd8002000
[17180961.760000] saa7134[1]: subsystem: 16be:0005, board: Medion 7134 Bridge #2 [card=93,autodetected]
[17180961.760000] saa7134[1]: board init: gpio is 0
[17180961.760000] saa7134[1]: Medion 7134 Bridge #2: dual saa713x broadcast decoders
[17180961.760000] saa7134[1]: Sorry, none of the inputs to this chip are supported yet.
[17180961.760000] saa7134[1]: Dual decoder functionality is disabled for now, use the other chip.
[17180961.900000] saa7134[1]: i2c eeprom 00: be 16 05 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17180961.900000] saa7134[1]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[17180961.900000] saa7134[1]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 21 02 51 96 2b
[17180961.900000] saa7134[1]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[17180961.900000] saa7134[1]: i2c eeprom 40: ff 24 00 c0 ff 1c 00 ff ff ff fd 79 44 9f c2 8f
[17180961.900000] saa7134[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180961.900000] saa7134[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180961.900000] saa7134[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180961.908000] saa7134[1]: registered device video1 [v4l2]
[17180961.908000] saa7134[1]: registered device vbi1
[17180961.916000] saa7134 ALSA driver for DMA sound loaded
[17180961.916000] saa7134[0]/alsa: saa7134[0] at 0xd8000000 irq 225 registered as card -1
[17180961.916000] saa7134[1]/alsa: saa7134[1] at 0xd8002000 irq 233 registered as card -1
```


I can use tvtime with /dev/video0 but all I can see are analog TV stations (without sound but that's another issue...)

With kaffeine I can't receive any channels, I don't even have an option to view DVB. :-k 

Can someone help me here please?

Thanks

Winger

---

