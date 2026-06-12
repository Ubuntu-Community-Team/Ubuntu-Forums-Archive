---
title: "Atheros card not detected properly"
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by kapiladhanvi on 2009-01-28
I have a Atheros card that is not being detected correctly in my system ( Ubuntu 8.10 ). It is being detected I presume as C. P. Technologies.

how can I fix this ?? 

lspci command -

```

00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP78S [GeForce 8200] LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation Device 0ad0 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP78S [GeForce 8200] Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h [Opteron, Athlon64, Sempron] Link Control
01:08.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0a.0 Class c600: C.P. Technology Co. Ltd Device 001a (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8200 (rev a2)


```

Output from lshw -c Network -
```
*-network UNCLAIMED
description: Ethernet controller
product: C.P. Technology Co. Ltd
vendor: C.P. Technology Co. Ltd
physical id: a
bus info: pci@0000:01:0a.0
version: 01
width: 32 bits
clock: 33MHz
configuration: latency=32 maxlatency=28 mingnt=10
*-network
description: Ethernet interface
product: MCP78S [GeForce 8200] Ethernet
vendor: nVidia Corporation
physical id: a
bus info: pci@0000:00:0a.0
logical name: eth0
version: a2
serial: 00:30:1b:bc:f5:49
capacity: 1GB/s
width: 32 bits
clock: 66MHz
capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
```

I have uploaded the output from lsmod with this post.

It would be great if someone could help me get my wifi working ??

thanks,
Dhanvi

---

### Post by kapiladhanvi on 2009-01-28
Can someone PLEASE help me with my problem ?? :( I would be very grateful for the same.. 

Dhanvi

---

### Post by teh_drizzle on 2009-07-20
Were you ever able to solve the issue? 

I popped in the Live CD (9.04) into a machine with the nVidia Corporation MCP78S Ethernet card. There was no Ethernet (eth0) device found, just a loop back. I didn't have time to try any fixes as working without a network is very frustrating xD. 

I plan on looking into it more later tonight, starting with a new ubuntu kernel.

---

### Post by kapiladhanvi on 2009-07-20
I wasn't able to resolve it with then. I tried to follow most of the results on the forums but did not help me. The card was not being detected. 

I finally upgraded to the new 9.04 and that looks to have solved that issue sometime back when I logged into that system. 

Dhanvi

---

