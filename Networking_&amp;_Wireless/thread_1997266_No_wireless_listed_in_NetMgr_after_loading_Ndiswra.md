---
title: "No wireless listed in NetMgr after loading Ndiswrapper and Win7 driver  in UB12.04"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by vbasic246 on 2012-06-04
I have an Acer 5552-5898 laptop (**64-bit AMD CPU**). I am dual-booting "Win-7 (64-bit)" and *"Ubuntu 12.04 32-bit*". Wireless (& wired) works on Win-7, **_only wired_** works on UB12.04.

My home wireless network was CONNECTED, but never working. I constantly got the message, 'Setting network address', and the wireless icon kept flickering on and off.

I loaded **Ndiswrapper**, **NdisGTK** and my **Win-7 Atheros AR5B97 wireless driver** per article ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)).

Per the article I added these lines to 'blacklist.conf':

# added by on 6-4-2012
blacklist ath_pci
blacklist ath_hal
blacklist b43
blacklist b43legacy
blacklist ssb

[COLOR=Blue]After rebooting, Network Manager does not display "Wireless networks" and "Enable wireless".  One command's output in the Terminal says 'l0, eth0 - No wireless extensions'.[/COLOR]

[COLOR=Red]I need help getting my wireless working in Network Manager?[/COLOR]

Thank you in advance.
[vbasic246]

Here's the output of the 'lspci' command:

~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RS880M [Mobility Radeon HD 4200 Series]
01:05.1 Audio device: Advanced Micro Devices [AMD] nee ATI RS880 HDMI Audio [Radeon HD 4200 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
08:00.0 Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
~$

---

### Post by chili555 on 2012-06-05
From the link you quoted:>     Important: Be careful when using the drivers from the CD included with the wireless card. They may work and you can try them, but you could experience kernel crashes and other serious problems if the driver on your CD has not been tested with ndiswrapper. 

    You should download a tested** Windows XP driver** which is suitable for your card from the ndiswrapper list. Post back if you need additional guidance or if you'd like to troubleshoot the native *ath9k* driver.

---

