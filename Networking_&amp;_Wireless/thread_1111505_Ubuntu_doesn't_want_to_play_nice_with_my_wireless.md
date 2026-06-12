---
title: "Ubuntu doesn't want to play nice with my wireless"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by Mr A Mouse on 2009-03-30
Yet another one for the list....

HP Pavillion dv6000. Clean install of Intrepid, and I added the headers and backports. ifconfig gives me eth0 and lo, but nothing for wireless.

lspci gives me:
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


iwconfig:
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

"Hardware Drivers" shows "Support for 5xxx series of Atheros 802.11 wireless LAN cards" and "Support for Atheros 802.11 wireless LAN cards," both are indicating that they are active and in use.

Help? Oh, unfortunately, any specific command output will have to wait until tomorrow: I don't have internet at home. :(

---

### Post by Mr A Mouse on 2009-03-30
I have a troubleshooting path: I found the following:

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

Wish me luck!

---

### Post by sgosnell on 2009-03-30
No wireless?  How about this line?

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg **Wireless** PCI Express Adapter (rev 01)

I think you need the ath5k driver for that.  I don't remember much about HP Pavilions, I gave mine away some time back, and never tried to run Linux on it.

---

### Post by Mr A Mouse on 2009-03-30
Success! Blacklisting the older Atheros drivers (per step 1 of the linked page) allowed me to connect.

> I think you need the ath5k driver for that.

I had it installed, but evidently the older Atheros drivers and the newer one don't play nice together.

/me does the happy dance....

/me realizes mice can't dance....

/me shuffles off, stage left....


:D

---

### Post by TBerk on 2009-03-30
I think you'll want to preface the Subject line (title) with a [SOLVED] label.

Thx for appending with a solution.


TBerk

---

