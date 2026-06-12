---
title: "Wireless and ndiswrapper works, but won't stay functional"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by MattP220 on 2009-01-05
Hi,

I'm running 8.04 on a dual-boot with Vista, AMD64 chip and 64-bit Ubuntu build. Wireless card is an Atheros AR242x, currently running the net5211 driver installed through ndiswrapper. 

Okay, so this arrangement is actually functional. With the Linux drivers blacklisted and turned off, this driver does actually work without problems. 

The problem is, it doesn't stay that way. When I reboot, I have to uninstall and then reinstall the driver in the ndisgtk program. That makes it work again.

Obviously I don't want to have to do this each and every time I boot into Ubuntu. I did search the ndiswrapper troubleshooting thread and in this forum in general, but I didn't come up with anything that touched on this exact issue. 

Here's system info:

```
lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:64:0e:09
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e2:a1:b7:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 ip=192.168.1.100 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
```

```
lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)
```


```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:64:0e:09  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1484 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:970859 (948.1 KB)  TX bytes:970859 (948.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e2:a1:b7:9d  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e2ff:fea1:b79d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80927 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:100791740 (96.1 MB)  TX bytes:6800349 (6.4 MB)
          Interrupt:19 Memory:f6000000-f6010000 
```

---

### Post by josefcarel on 2009-01-05
Try to do that
**sudo gedit /etc/modules**

at the end of the file write:
**ndiswrapper**
Save and reboot

I hope it will help you

---

### Post by MattP220 on 2009-01-05
Hi josef,

I just opened up /etc/modules, and ndiswrapper was already at the end of the file.

It seems that ndiswrapper will load properly, but there is some kind of configuration error that requires the driver be reloaded.

---

### Post by josefcarel on 2009-01-12
> **MattP220 said:**
> Hi josef,

I just opened up /etc/modules, and ndiswrapper was already at the end of the file.

It seems that ndiswrapper will load properly, but there is some kind of configuration error that requires the driver be reloaded.

Im sorry I cant help you more. There is also in this file: ath_pci ?

Look also if ndiswrapper is still there.

Hope to be more useful.

---

### Post by HunterThomson on 2009-01-12
You mite have better luck with the linux native MadWiFi drivers.

---

