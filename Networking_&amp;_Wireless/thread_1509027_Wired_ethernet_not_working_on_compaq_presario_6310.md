---
title: "Wired ethernet not working on compaq presario 6310"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by duhfactor on 2010-06-13
Hi folks,

I acquired an older hp compaq presario computer version 6310us, and initially installed mint, followed by Ubuntu 9.04. Neither one recognized the onboard ethernet port. I checked the bios, and LAN is enabled. It is also enabled in the drop down menu from the toolbar on the desktop. The cable works fine on other computers, and the light on the ethernet port flashes like it does when the cable is connected. I'm new to linux, so not sure what to do to get the connection working. Any ideas??

D

---

### Post by duhfactor on 2010-06-13
bump?

---

### Post by anthonylane13 on 2011-06-25
I have the same problem on a Compaq Presario SR5019UK...

I even tried installing a separate PCI network card. I'm dual booting with windows (vista) and windows will happily connect from either network port. But ubuntu (and linux mint, Suse) simply won't connect.

Any advice much appreciated.

Here's my lspci:

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0d.0 VGA compatible controller: nVidia Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

