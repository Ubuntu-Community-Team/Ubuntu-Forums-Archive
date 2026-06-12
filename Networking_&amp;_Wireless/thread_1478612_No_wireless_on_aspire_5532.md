---
title: "No wireless on aspire 5532"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by mbrowning2000 on 2010-05-09
Hi guys,

  I just installed Ubuntu 10.04 x64 on my Aspire 5532, and almost everything works, there is just 1 thing....My Wireless doesn't seem to work, or I'm just a dummy that don't know how to connect to wireless in ubuntu...

here is the output of lspci:

michael@michael-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
**02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)**
08:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0) 

if u need any more info just ask

Thanks for any help

---

### Post by pastalavista on 2010-05-10
If possible, connect your PC to the internet via ethernet (wired) and use the Hardware Drivers tool in the System/Administration menu to automatically download and install the drivers for your wireless card.

---

### Post by bkratz on 2010-05-10
> **mbrowning2000 said:**
> 

[B]02:00.0 Network controller: Broadcom Corporation Device 4357 (rev 01)


Following pastalavista's advice is correct, just adding for future reference that your card is functional with the STA driver which if you look at the readme file

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

you will see it last in the list.

---

### Post by mbrowning2000 on 2010-05-10
Problem Solved....Thanks for your help guys.

---

### Post by bkratz on 2010-05-10
> **mbrowning2000 said:**
> Problem Solved....Thanks for your help guys.

Congratulations!--
I'm sure a lot of others would be interested in exactly what your solution was. You might let us know and mark the thread as [solved] in the thread tools above.

---

