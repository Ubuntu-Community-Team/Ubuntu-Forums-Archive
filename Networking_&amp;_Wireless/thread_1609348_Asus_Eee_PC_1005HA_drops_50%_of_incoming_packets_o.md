---
title: "Asus Eee PC 1005HA drops 50% of incoming packets over wifi"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by dave1010 on 2010-10-30
Hi,

Pinging out from my netbook (over wifi, to any host) gets ~0% packet loss. Pinging into it (from any host) gets about 50% packet loss. 

The router is a Dlink-DIR615 (rev d, running DD-WRT v24-sp2) but all other hosts on it ping eachother fine. I've tried changing routing, disabling IPv6, using older kernels and using wicd, all with no luck. The wireless connections is at 100% most of the time. This could be a new problem with Maverick, but I may not have noticed it before. I believe this is causing web browsing to be really slow and causing SSH timeouts.

I haven't tried madwifi drivers or nsidwrapper yet. Are they worth a go? Any other ideas?

Edit: just booted into Windows and it has the same problem. Could it be a hardware issue? Also tried with a static IP, with no change.

Strangely, a normal ping gets 50% packet loss, but ping -A gets < 1% loss.

Edit 2: no packet loss at all on eth0.

```
# uname -a
Linux hulbert-laptop 2.6.35-23-generic #36-Ubuntu SMP Tue Oct 26 17:03:18 UTC 2010 i686 GNU/Linux
``````
# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:25:d3:1a:bc:4b  
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe1a:bc4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11944 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11612998 (11.6 MB)  TX bytes:1751538 (1.7 MB)
``````
# iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"44g"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 1C:AF:F7:43:79:B4   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 4 [8086:27d6] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8132 Fast Ethernet [1969:1062] (rev c0)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
``````
# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
``````
# lshw -C Network
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:25:d3:1a:bc:4b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-23-generic firmware=N/A ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 00:26:18:4d:5f:0a
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
```

---

### Post by theonhighgod on 2010-11-01
I haven't had much luck with the mad wifi my self, in fact I had a problem a lot like your one when I used mad wifi for a bit. The fact its happening in windows to me suggests a router and your asus issue. What happens around friends places? any other devices on your network? 

maybe tracepath may give you a hint as to where the problem lies.

could try updating the firmware on your router? (be careful with that if you do)

hope else is well in life

---

