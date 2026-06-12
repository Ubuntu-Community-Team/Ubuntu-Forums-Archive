---
title: "Trying to get ndiswrapper to claim wireless card"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by xenocution on 2009-04-30
Trying to get my Netgear WG311v3 wireless card working. Ndiswrapper will install the drivers, but I can not get it to claim the card or get the card to detect.

I would like to make the wireless card "wlan0" as well. I think there is a conflict with the wire ethernet on "eth0".

The wireless card is the "Marvell Technology Group Ltd."
The wire ethternet is the "VIA Technologies, Inc."

Kubuntu 9.04

> **lshw -C network:**
 
*-network:0 UNCLAIMED
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
  
*-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:6e:52:a2:ce
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  
*-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 32:45:3f:b9:02:d6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes



**lspci -nn:**

00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge [1106:3116]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP] [1106:b091]
00:0a.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless [11ab:1faa] (rev 03)
00:0b.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 07)
00:0b.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 07)
00:10.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 80)
00:10.3 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 82)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8235 ISA Bridge [1106:3177]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 74)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV44A [GeForce 6200] [10de:0221] (rev a1)



**ifconfig -a:**

eth0      Link encap:Ethernet  HWaddr 00:0c:6e:52:a2:ce
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2e00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3288 (3.2 KB)  TX bytes:3288 (3.2 KB)

pan0      Link encap:Ethernet  HWaddr 32:45:3f:b9:02:d6
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



**ndiswrapper -l:**

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
        device (11AB:1FAA) present



Thanks for any help I can get on this. :)

---

### Post by xenocution on 2009-05-01
Found the following commands and ran them:

> depmod -a
modprobe ndiswrapper
ndiswrapper -mi
ndiswrapper -m
depmod -a modprobe ndiswrapper

My wireless seems to be working now. Just thought I'd post the solution I found for others.

---

