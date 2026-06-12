---
title: "how to know video card interface??"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by zjcim on 2006-08-13
i have a laptop IBM x24 with ati video card.
which interface does the card use?? AGP or PCI

lspci i get ```
0000:00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 04)0000:00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)0000:00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)0000:00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #3) (rev 02)0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:03.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
0000:02:03.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev a8)
0000:02:03.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller
0000:02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)

```

btw,is ait mobility m6 ly ati mobility 7500 or ati mobility 9000
thx

---

### Post by foolsh on 2006-08-13
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
this is your video card at pci busid 1:00:00

---

### Post by zjcim on 2006-08-14
so ,what does the agp bus look like if there's agp bus in intel 830mp chipset??

---

### Post by zxee on 2006-08-14
> **zjcim said:**
> so ,what does the agp bus look like if there's agp bus in intel 830mp chipset??

An AGP slot is just a specialized PCI slot. e.g I have a homebuilt desktop with an AGP slot and lspci -v produces similar results to what you posted. In other words if you had both a PCI & AGP video card lspci -v would show them both.

---

