---
title: "Amilo sa 3650 Ubuntu 9.10 bad wireless connection, not only in browser"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by Antiverminseed on 2010-02-21
Hi there

i recently installed ubuntu 9.10 on my Fujitsu Siemes Amilo sa 3650 and after updating my BIOS i got my wireless card to work but very slowly. I thought it could be a problem with firefox so i read something about changing firefox to auto detect proxy. It might have helped some but I noticed bad connection when I was updating sofware in update-manager and using streaming programs like Spotify as well so obviously that wasn't the real problem.

i don't know the name of my wireless card but i read something about writing "lspci" in the terminal. So i did and got this:

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:03.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 1)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
0e:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
0f:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
10:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
10:00.1 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
10:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller
10:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
10:00.4 System peripheral: JMicron Technology Corp. xD Host Controller

```


Any ideas? I'm sorry if this is something of a beginners question and I will continue reading different guides and make sure I read all the "beginners stuff" so i don't post unnecessary questions in the future, i just got so tired of looking for answers and getting really confused by them because i don't understand the terminology. 

Thanks in advance!

---

