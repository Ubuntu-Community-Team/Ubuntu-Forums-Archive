---
title: "Wireless Connection Issue"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by Swanny2010 on 2010-07-30
Hey guys need abit of help since im new to ubuntu :D.

Soo i just installed Wubi ( ubuntu installer for windows ) and ive got a problem with my wireless :(.

The button on my laptop to turn the wireless on shows that my wireless is turned off ( orange light ) when i try turn it on the light should go blue but it just stays orange like its not turned on.

On ubuntu i looked on the driver folder thing :p, and theres nothing there at all. Not sure really what to do tbh..

I know my wireless is built in to my laptop and its a broadcom 802.11g network adapter.

Its on the same laptop as im writing this on so i need to keep restarting to go on wubi.


Any help please?

---

### Post by Swanny2010 on 2010-07-30
Help please :(

---

### Post by viking350 on 2010-07-30
first i have to say wubi is trouble wish i could help but i do not know anything about wubi

---

### Post by viking350 on 2010-07-30
but try burning it on a cd then going into it install and do it by partitioner see if that helps

---

### Post by Swanny2010 on 2010-07-30
it should still work tho like this hmm..
i ran the things in terminal for my wireless stuff..


michael@ubuntu:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge 
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) 
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) 
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) 
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4) 
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
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40) 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10) 
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev ff) 
michael@ubuntu:~$ 







  *-network                
       description: Ethernet interface 
       product: Marvell Technology Group Ltd. 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 10 
       serial: 00:24:81:4b:39:d5 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes 
       resources: irq:28 memory:53100000-53103fff ioport:3000(size=256) 
  *-network DISABLED 
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:21:00:ba:ff:f0 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg 
michael@ubuntu:~$

---

### Post by Swanny2010 on 2010-07-30
hmm so much for ubuntu being easy and simple

---

### Post by Swanny2010 on 2010-07-30
help please :(

---

