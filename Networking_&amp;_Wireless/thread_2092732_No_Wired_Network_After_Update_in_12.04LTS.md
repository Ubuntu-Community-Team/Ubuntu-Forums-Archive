---
title: "No Wired Network After Update in 12.04LTS"
date: 2012-12-08
forum: Networking &amp; Wireless
---

### Post by Drafthorse304 on 2012-12-08
I'm running Ubuntu 12.04LTS 64-bit on an Asus A53Z series laptop. After the last kernel update my **wired network** connections are dead. The wireless networking works fine. 

Network manager shows "Wired Network" grayed out, and does not sense when the network cable is connected or disconnected. Both wired and wireless network interfaces worked fine in Windows 7, and I used wired before the last kernel update. I'm thinking that a config file or something got hosed in the update, but am not certain where to look. 

**Output from lspci:**
```
bruces@Stripes:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9647
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:02.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03)
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.7 SD Host controller: Advanced Micro Devices [AMD] Hudson SD Flash Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
**02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)**
03:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)

```[B]

Output of lshw -C network:
[/B]
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: 10:bf:48:47:13:42
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:46 ioport:e000(size=256) memory:d0004000-d0004fff memory:d0000000-d0003fff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:12:f7:32
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-34-generic firmware=N/A ip=192.168.11.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fea00000-fea7ffff memory:fea80000-fea8ffff

```[B]

Output of ifconfig -a:[/B]
```
bruces@Stripes:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 10:bf:48:47:13:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:367246 (367.2 KB)  TX bytes:367246 (367.2 KB)

wlan0     Link encap:Ethernet  HWaddr 44:6d:57:12:f7:32  
          inet addr:192.168.11.5  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::466d:57ff:fe12:f732/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56964 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45091 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71197621 (71.1 MB)  TX bytes:5477673 (5.4 MB)

```

eth0 shows no inet addr lines, so I'm thinking I need help following this to see where it goes. Thanks for any help.

---

### Post by Drafthorse304 on 2012-12-08
Found the solution to this problem in a round about way. The problem boiled down to the wrong NIC driver being loaded. 

```
bruces@Stripes:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:107c]
    Kernel driver in use: **r8169**

```I have an 8168 NIC, so the number matters. :)

Found the answer for the driver problem in this post: [http://ubuntuforums.org/showpost.php?p=12333294&postcount=5](http://ubuntuforums.org/showpost.php?p=12333294&postcount=5)

and followed the directions there. The wired network interface came up as soon as the proper driver module was loaded. Rebooted per the instructions just in case, but the problem seems to be cleared up now.

**lspci -nnk | grep -iA2 net** now shows:

```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device [1043:107c]
    Kernel driver in use: **r8168**

```Cheers.

---

### Post by Drafthorse304 on 2012-12-21
Quick update:

This driver problem came back after the last kernel update. :confused:  I have an Realtek 8168 series ethernet NIC and the 8169 series driver was loaded again. 

The Good news is the solution for it is the same. Got the 8168 driver, compiled it per instructions, and it works.

---

