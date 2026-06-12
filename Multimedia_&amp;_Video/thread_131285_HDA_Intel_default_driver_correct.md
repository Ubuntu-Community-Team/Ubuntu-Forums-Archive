---
title: "HDA Intel default driver correct?"
date: 2006-02-16
forum: Multimedia &amp; Video
---

### Post by dennisgodderie on 2006-02-16
I nearly new to ubuntu, but did managed to get everything working fine (including prgorams). The only thing that doesn't work is sound :)

If i go to the sound option I see "Default soundcard: HDA intel".
I don't know if this is correct? Is there any way you can check that?

Thanks

---

### Post by christhemonkey on 2006-02-16
If you have a pci sound card:
```
lspci
```

---

### Post by dennisgodderie on 2006-02-17
lspci give me this:

root@dennisglaptop:/home/dennis# lspci
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. Mobile Memory Controller Hub PCI Express Po rt (rev 03)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definiti on Audio Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB  UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Contro ller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0168 (rev a1)
0000:06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
0000:06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two -Port PHY/Link-Layer Controller
0000:06:03.3 Unknown mass storage controller: Texas Instruments PCI7420/PCI7620 Dual Socket CardBus and Smart Card Cont. w/ 1394a-2000 OHCI Two-Port  PHY/Link-L ayer Cont. an
0000:06:04.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
0000:06:08.0 Ethernet controller: Intel Corp.: Unknown device 1068 (rev 03)

---

