---
title: "LAN card is not working in Ubuntu 10.04"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by ashickur.noor on 2011-04-15
I am naive user of Ubuntu and I am using Ubuntu 10.04 for last 9 months. 
I have a switch my Asus F80q laptop with Toshiba L650D Laptop.

In my new laptop LAN card is not working. When plug a cable in the LAN card it show me connected but I not connected in Internet or my local networks. I have configure the IP address, net mask, getway DNS server address but still not working. 

Please anybody help me ASAP.
Here is the output of lspci command > 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)

---

### Post by chili555 on 2011-04-15
> I have configure the IP address, net mask, getway DNS server address but still not working.How about letting us see those numbers?

---

### Post by ashickur.noor on 2011-04-15
> **chili555 said:**
> How about letting us see those numbers?
ip:192.168.0.254
net mask: 255.255.255.0
get way : 192.168.0.1
DNS : 124.109.16.7,124.109.16.11

---

### Post by chili555 on 2011-04-15
The IP address 192.168.0.254 is usually reserved for routers. I don't know for sure that you absolutely can't use it for a client machine, but let's just try changing your IP address to 192.168.0.250. You will probably need to reboot and then try:```
ifconfig eth0
```Did you get the x.250 address? Now try:```
ping -c3 192.168.0.1
ping -c3 www.google.com
```

---

### Post by ashickur.noor on 2011-04-15
chili555 Please just forget about connect in INTERNET. When I try to share data between 2 Pc's using LAN then it also not works. I think my problem is in LAN card not in ip addresses.

More over I am using *.254 about 1 year in my University lab.  And in my Asus F80q it works fine enpugh.

---

