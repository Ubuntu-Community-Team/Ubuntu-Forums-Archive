---
title: "sound difficulties"
date: 2008-09-29
forum: Multimedia Software
---

### Post by niteklub79 on 2008-09-29
HELP!!!

I have use Ubuntu since 7.10 and have installed 8.04 - there was and is only one problem my on-board soundcard is not being recognized.

I was able to access my system bios ONCE and activated the contollers for the soundcard, however after I rebooted the system failed to recognize my activated on-board sound card.

when I work in terminal the response is that there are no soundcards
I cannot access my system bios

what can/should i do?

---

### Post by Crafty Kisses on 2008-09-29
What are the results of this output?
```
lspci
```

---

### Post by niteklub79 on 2008-09-30
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:0e.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
00:12.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)


- hope this helps

---

