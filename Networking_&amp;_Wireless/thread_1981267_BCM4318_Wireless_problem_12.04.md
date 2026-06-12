---
title: "BCM4318 Wireless problem 12.04"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by facepipe on 2012-05-16
I have a Dell inspiron 1300 with a Broadcom b43 BCM4318 Wifi card. I am trying to install 12.04 but the installer crashes every time I load it. Tried a few things and discovered that disabling the minipci slot where the BCM4318 sits and ubuntu installs. I tried it with Debian Squeeze and it installed no probs with the card on and the card worked.
I can install Ubuntu with the minipci slot off but when i turn it on again Ubuntu fails to boot.

---

### Post by facepipe on 2012-05-16
Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
        Subsystem: Dell Wireless 1370 WLAN Mini-PCI Card [1028:0005]
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at dfbfe000 (32-bit, non-prefetchable) [size=8K]

---

### Post by mörgæs on 2012-05-16
Moved to Networking. 
Please also see the sticky notes in this forum.

---

### Post by facepipe on 2012-05-16
Thanks had a look at the sticky but as this issue prevents ubuntu from installing or booting I am not able to do most of the troubleshooting listed.

---

### Post by facepipe on 2012-05-16
lspci -nn output with card turned off.

```
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express                                                                                                                                Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910                                                                                                                               GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Exp                                                                                                                               ress Graphics Controller [8086:2792] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Famil                                                                                                                               y) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family)                                                                                                                                PCI Express Port 1 [8086:2660] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family)                                                                                                                                PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Fam                                                                                                                               ily) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Fam                                                                                                                               ily) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Fam                                                                                                                               ily) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Fam                                                                                                                               ily) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Fam                                                                                                                               ily) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448]                                                                                                                                (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Brid                                                                                                                               ge [8086:2641] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Fami                                                                                                                               ly) IDE Controller [8086:266f] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [                                                                                                                               14e4:170c] (rev 02)

```

---

### Post by facepipe on 2012-05-16
followed these instructions with card off and rebboted with card om [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access)

---

