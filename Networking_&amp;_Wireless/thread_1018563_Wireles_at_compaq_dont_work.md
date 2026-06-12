---
title: "Wireles at compaq dont work"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by Padde999 on 2008-12-22
Hallo there. can anyone help me with a problem.

I have compaq and have several times try to instal ubuntu, and now i try it againd with the new 8.10. But my wireles lan whil not work.

---

### Post by tigerstripedcat on 2008-12-22
So you cannot connect to your wireless router?  If you open up a console and type in "iwlist scan" does it show any APs?  Do you even see something that says "ra0" "wifi0" or "wlan0"?  If not you don't have a kernel module loaded to support your wifi.

---

### Post by Ayuthia on 2008-12-22
Can you post the results of lspci -nn from the Terminal?  We need to figure out what wireless card you have.

---

### Post by Padde999 on 2009-01-06
it can not find anything

in "iwlist scan"

lo    Interface doesn't support scanning

eth0  Interface doesn't support scanning

pan0  Interface doesn't support scanning



but the lan card is a Atheros 802.11

---

### Post by Padde999 on 2009-01-06
In "lspci -nn"


00:00.0 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0754] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation Device [10de:075e] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP78S [GeForce 8200] SMBus [10de:0752] (rev a1)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP78S [GeForce 8200] Co-Processor [10de:0753] (rev a2)
00:01.4 RAM memory [0500]: nVidia Corporation MCP78S [GeForce 8200] Memory Controller [10de:0568] (rev a1)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077b] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077c] (rev a1)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller [10de:077d] (rev a1)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller [10de:077e] (rev a1)
00:06.0 IDE interface [0101]: nVidia Corporation MCP78S [GeForce 8200] IDE [10de:0759] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec [10de:0774] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge [10de:075a] (rev a1)
00:09.0 IDE interface [0101]: nVidia Corporation Device [10de:0ad0] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP78S [GeForce 8200] Ethernet [10de:0760] (rev a2)
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge [10de:0569] (rev a1)
00:14.0 PCI bridge [0604]: nVidia Corporation Device [10de:077a] (rev a1)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration [1022:1300] (rev 40)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Address Map [1022:1301]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h DRAM Controller [1022:1302]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control [1022:1303]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 11h Link Control [1022:1304]
02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0845] (rev a2)
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

---

