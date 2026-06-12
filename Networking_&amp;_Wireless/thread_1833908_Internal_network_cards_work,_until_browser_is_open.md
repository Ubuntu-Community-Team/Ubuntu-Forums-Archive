---
title: "Internal network cards work, until browser is opened."
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by Nohbudy on 2011-08-26
Hello, 
I am having a strange issue that I cannot find help elsewhere about. 

About a month after installing ubuntu a problem started where If I plug my computer in through the internal Ethernet port (eth0) into a network, and open my browser; the network will lock up after loading 2-3 websites. The only way to release the locked network, is to completely restart. If I use network manager to disable the device or networking, It doesn't do anything.

Here's where it gets funny. I can plug in ethernet, connect to the internet, SSH, FTP, IRC, Play games like minecraft and so on as long as I don't open a web browser. It doesn't matter what browser, I tried chrome and firefox and they both lock up the network.

Not sure if it's related or not, but it started at the same time. Wireless will lock the entire machine if it's able to even load the driver. Before this issue began, I had no problems using either wifi or ethernet.

I experience this problem with fresh Ubuntu 11.04 disks, Debian live CD's, and on my install of Debian (Previously ubuntu, I want to switch back to ubuntu but it's got the Wifi driver that crashes before I can even start the install)

Thanks for your help!

Some basic information
Device: Toshiba Satalite C655D-S5143
Wifi: Realtek RT8188CE (Rev 1)
eth0: Atheros AR8152 v2.0 (Rev c1)

64 Bit Debian Squeeze / Ubuntu 11.04

I'm attaching my lspci
```

00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1510
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9803
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: ATI Technologies Inc Device 43a0
00:15.1 PCI bridge: ATI Technologies Inc Device 43a1
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
06:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)

```

---

### Post by praseodym on 2011-08-26
Did you try some boot-parameters like "acpi=off", "nomodeset" or "pci=noacpi"?

---

