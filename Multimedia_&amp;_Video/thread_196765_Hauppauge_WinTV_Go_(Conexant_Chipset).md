---
title: "Hauppauge WinTV Go (Conexant Chipset)"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by DoddyUK on 2006-06-14
This is an update of a thread I made a few weeks back. I've installed Kubuntu 6.06 Dapper, and I was pleasantly surprised to see that I was able to get a video output from the card via the composite input, and through the aeriel after watching TV in windows (defaults to the last channel I watched). 

However, I still don't have the ability to change channels or tune into any other stations. Here's the output from my Dmesg:

```

[4294697.348000] Linux video capture interface: v1.00
[4294697.468000] cx2388x v4l2 driver version 0.0.5 loaded
[4294697.469000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 18 (level, low) -> IRQ 185
[4294697.469000] CORE cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx models [card=1,autodetected]
**[4294697.469000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe**
[4294697.570000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> GSI 17 (level, low) -> IRQ 193
[4294697.570000] rt2500 1.1.0 BETA3 2005/07/31 http://rt2x00.serialmonkey.com
[4294697.602000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294697.723000] tveeprom 0-0050: Hauppauge model 34705, rev J198, serial# 8507373
**[4294697.723000] tveeprom 0-0050: tuner model is TCL 2002MI_3H (idx 98, type 4)**
[4294697.723000] tveeprom 0-0050: TV standards PAL(I) PAL(D/K) (eeprom 0x50)
[4294697.723000] tveeprom 0-0050: audio processor is CX881 (idx 31)
[4294697.723000] tveeprom 0-0050: has radio
**[4294697.723000] cx88[0]: warning: unknown hauppauge model #34705**
[4294697.723000] cx88[0]: hauppauge eeprom: model=34705
[4294697.723000] input: cx88 IR (Hauppauge WinTV 34xxx  as /class/input/input1
[4294697.723000] cx88[0]/0: found at 0000:00:0b.0, rev: 5, irq: 185, latency: 32, mmio: 0xde000000
[4294697.931000] Real Time Clock Driver v1.12
[4294697.980000] Linux agpgart interface v0.101 (c) Dave Jones
[4294698.001000] agpgart: Detected VIA KM400/KM400A chipset
[4294698.007000] via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
[4294698.011000] agpgart: AGP aperture is 128M @ 0xd0000000
[4294698.079000] Floppy drive(s): fd0 is 1.44M
[4294698.093000] FDC 0 is a post-1991 82077
[4294698.461000] cx88[0]/0: registered device video0 [v4l2]
[4294698.461000] cx88[0]/0: registered device vbi0
[4294698.461000] cx88[0]/0: registered device radio0

```

I find it strange that the tuner is initially set as **-1**, but then names the tuner as **"tuner model is TCL 2002MI_3H (idx 98, type 4)"**. I have a feeling I might have to explicitly set the tuner number, but I just want to ask what you guys think first.

Cheers

---

