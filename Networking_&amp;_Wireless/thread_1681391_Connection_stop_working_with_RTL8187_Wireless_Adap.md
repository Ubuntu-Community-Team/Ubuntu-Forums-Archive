---
title: "Connection stop working with RTL8187 Wireless Adapter after few minuts"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by galorian on 2011-02-04
Hi guys :)

I'll start saying that i have read MANY topics regarding rtl8187 and tryied their solutions - with no success. I'm not a noob  but I'm totaly stuck with this issue.

The Problem:
I buy a new usb network adapter (Through DX), when I try to use it in ubuntu or BackTrack4 Final it is working, and connecting networks even with WPA encryption.
But after few minuts it stops working totally. It is showing that I'm connected to the AP but web sites do not respond.

Notes:
- I have another PCI Wireless adapter which works fine.
- The problematic adapter works great on windows.
- A driver CD came with it, including a linux driver which I wasn't succesfully installed.
- A BackTrack3 Disc came with it, claming by the instructions that the adapter will work with it. I didn't try it because i have backtrack 4 final.


It took me dozens of surfing the web hours, and too many restarts,

Many thanks to helpers!

---

### Post by galorian on 2011-02-04
Sorry 
saw the sticky thread
i'll read it and post my qustion a littel later

---

### Post by galorian on 2011-02-04
OK guys! :)

Here some rellevant INFO,

I would really appricihet help!

iwconfig
The Problematic InterFace is wlan1
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ADV"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:B0:E8:9C:11   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"\x02\x1A\xFEC\xFB\xFA\xAA:\xFB)\xD1\xE6\x05<|\x94u\xD8\xBEa\x89\xF9\\xBB\xA8\x99\x0F\x95\xB1\xEB\xF1\xB3"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:50:fc:b0:f0:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4527 (4.5 KB)  TX bytes:4527 (4.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:9a:60:e1  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe9a:60e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13897271 (13.8 MB)  TX bytes:2897288 (2.8 MB)

wlan1     Link encap:Ethernet  HWaddr 00:e0:0c:e0:da:41  
          inet6 addr: fe80::2e0:cff:fee0:da41/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3186610 (3.1 MB)  TX bytes:566448 (566.4 KB)

```lspci
```

...
02:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI
...

```lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```dmesg
I gave just the end of it where I saw things like WLAN*. is it OK? :)
```
[   27.889740] ISO 9660 Extensions: Microsoft Joliet Level 3
[   27.894597] ISOFS: changing to secondary root
[   33.365076] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[   33.365104] wlan0: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[   33.365143] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[   33.368755] wlan0: direct probe responded
[   33.368764] wlan0: authenticate with AP 00:22:b0:e8:9c:11 (try 1)
[   33.370595] wlan0: authenticated
[   33.370647] wlan0: associate with AP 00:22:b0:e8:9c:11 (try 1)
[   33.373153] wlan0: RX AssocResp from 00:22:b0:e8:9c:11 (capab=0x411 status=0 aid=2)
[   33.373160] wlan0: associated
[   33.374079] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   43.556012] wlan0: no IPv6 routers present
[  239.220112] usb 1-2: new high speed USB device using ehci_hcd and address 3
[  239.359036] usb 1-2: configuration #1 chosen from 1 choice
[  239.627427] phy1: Selected rate control algorithm 'minstrel'
[  239.629270] phy1: hwaddr 00:e0:0c:e0:da:41, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  239.643738] rtl8187: Customer ID is 0x00
[  239.644000] Registered led device: rtl8187-phy1::tx
[  239.649336] Registered led device: rtl8187-phy1::rx
[  239.652691] rtl8187: wireless switch is on
[  239.653329] usbcore: registered new interface driver rtl8187
[  241.693302] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  250.317021] No probe response from AP 00:22:b0:e8:9c:11 after 500ms, disconnecting.
[  250.704890] wlan1: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[  250.813776] wlan1: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[  250.817903] wlan1: direct probe responded
[  250.817907] wlan1: authenticate with AP 00:22:b0:e8:9c:11 (try 1)
[  250.820273] wlan1: authenticated
[  250.820303] wlan1: associate with AP 00:22:b0:e8:9c:11 (try 1)
[  250.822773] wlan1: RX AssocResp from 00:22:b0:e8:9c:11 (capab=0x411 status=0 aid=2)
[  250.822778] wlan1: associated
[  250.825084] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  251.718112] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[  251.916026] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 2)
[  252.116026] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 3)
[  252.118036] wlan0: direct probe responded
[  252.118040] wlan0: authenticate with AP 00:22:b0:e8:9c:11 (try 1)
[  252.119796] wlan0: authenticated
[  252.119842] wlan0: associate with AP 00:22:b0:e8:9c:11 (try 1)
[  252.122305] wlan0: RX AssocResp from 00:22:b0:e8:9c:11 (capab=0x411 status=0 aid=4)
[  252.122314] wlan0: associated
[  261.732017] wlan1: no IPv6 routers present
[  264.672088] wlan0: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[  347.936129] wlan1: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[  360.132764] wlan1: deauthenticating from 00:23:cd:12:2e:e0 by local choice (reason=3)
[  360.346157] wlan1: direct probe to AP 00:23:cd:12:2e:e0 (try 1)
[  360.351076] wlan1: direct probe responded
[  360.351084] wlan1: authenticate with AP 00:23:cd:12:2e:e0 (try 1)
[  360.352897] wlan1: authenticated
[  360.352928] wlan1: associate with AP 00:23:cd:12:2e:e0 (try 1)
[  360.356091] wlan1: RX AssocResp from 00:23:cd:12:2e:e0 (capab=0x421 status=0 aid=2)
[  360.356101] wlan1: associated
[  449.629030] device wlan1 entered promiscuous mode
[  459.589059] device wlan1 left promiscuous mode
[  497.765042] wlan1: deauthenticating from 00:23:cd:12:2e:e0 by local choice (reason=3)
[  504.937673] wlan1: deauthenticating from 00:23:cd:12:2e:e0 by local choice (reason=3)
[  505.262160] wlan1: direct probe to AP 00:23:cd:12:2e:e0 (try 1)
[  505.275816] wlan1: direct probe responded
[  505.275823] wlan1: authenticate with AP 00:23:cd:12:2e:e0 (try 1)
[  505.288149] wlan1: authenticated
[  505.288189] wlan1: associate with AP 00:23:cd:12:2e:e0 (try 1)
[  505.291173] wlan1: RX AssocResp from 00:23:cd:12:2e:e0 (capab=0x421 status=0 aid=2)
[  505.291178] wlan1: associated
[  567.085045] wlan1: deauthenticating from 00:23:cd:12:2e:e0 by local choice (reason=3)
[  572.671123] wlan0: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[  572.869036] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[  573.068030] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 2)
[  573.070060] wlan0: direct probe responded
[  573.070065] wlan0: authenticate with AP 00:22:b0:e8:9c:11 (try 1)
[  573.071854] wlan0: authenticated
[  573.071902] wlan0: associate with AP 00:22:b0:e8:9c:11 (try 1)
[  573.075592] wlan0: RX AssocResp from 00:22:b0:e8:9c:11 (capab=0x411 status=0 aid=2)
[  573.075597] wlan0: associated
[  595.129031] device wlan0 entered promiscuous mode
[  612.401082] device wlan0 left promiscuous mode

```sudo lshw -C network
 ```
 *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 00
       serial: 00:0e:2e:9a:60:e1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=10.0.0.10 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:feaf8000-feafffff
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 86
       serial: 00:50:fc:b0:f0:96
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:b800(size=256) memory:feaf7c00-feaf7cff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:e0:0c:e0:da:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```iwlist wlan1 scan
```
wlan1     No scan results
```lsb_release -d
```
Description:    Ubuntu 10.04.2 LTS
```uname -mr
```
2.6.32-28-generic i686
```

---

### Post by dangerous666 on 2011-10-26
> **galorian said:**
> OK guys! :)

Here some rellevant INFO,

I would really appricihet help!

iwconfig
The Problematic InterFace is wlan1
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"ADV"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:B0:E8:9C:11   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     IEEE 802.11bg  ESSID:"\x02\x1A\xFEC\xFB\xFA\xAA:\xFB)\xD1\xE6\x05<|\x94u\xD8\xBEa\x89\xF9\\xBB\xA8\x99\x0F\x95\xB1\xEB\xF1\xB3"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:50:fc:b0:f0:96  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4527 (4.5 KB)  TX bytes:4527 (4.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:9a:60:e1  
          inet addr:10.0.0.10  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fe9a:60e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16868 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13897271 (13.8 MB)  TX bytes:2897288 (2.8 MB)

wlan1     Link encap:Ethernet  HWaddr 00:e0:0c:e0:da:41  
          inet6 addr: fe80::2e0:cff:fee0:da41/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3186610 (3.1 MB)  TX bytes:566448 (566.4 KB)

```lspci
```

...
02:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI
...

```lsusb
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2510 Pixart Imaging, Inc. Hama Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. RTL8187 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```dmesg
I gave just the end of it where I saw things like WLAN*. is it OK? :)
```
[   27.889740] ISO 9660 Extensions: Microsoft Joliet Level 3
[   27.894597] ISOFS: changing to secondary root
[   33.365076] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[   33.365104] wlan0: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[   33.365143] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[   33.368755] wlan0: direct probe responded
[   33.368764] wlan0: authenticate with AP 00:22:b0:e8:9c:11 (try 1)
[   33.370595] wlan0: authenticated
[   33.370647] wlan0: associate with AP 00:22:b0:e8:9c:11 (try 1)
[   33.373153] wlan0: RX AssocResp from 00:22:b0:e8:9c:11 (capab=0x411 status=0 aid=2)
[   33.373160] wlan0: associated
[   33.374079] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   43.556012] wlan0: no IPv6 routers present
[  239.220112] usb 1-2: new high speed USB device using ehci_hcd and address 3
[  239.359036] usb 1-2: configuration #1 chosen from 1 choice
[  239.627427] phy1: Selected rate control algorithm 'minstrel'
[  239.629270] phy1: hwaddr 00:e0:0c:e0:da:41, RTL8187vB (default) V1 + rtl8225z2, rfkill mask 2
[  239.643738] rtl8187: Customer ID is 0x00
[  239.644000] Registered led device: rtl8187-phy1::tx
[  239.649336] Registered led device: rtl8187-phy1::rx
[  239.652691] rtl8187: wireless switch is on
[  239.653329] usbcore: registered new interface driver rtl8187
[  241.693302] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  250.317021] No probe response from AP 00:22:b0:e8:9c:11 after 500ms, disconnecting.
[  250.704890] wlan1: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[  250.813776] wlan1: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[  250.817903] wlan1: direct probe responded
[  250.817907] wlan1: authenticate with AP 00:22:b0:e8:9c:11 (try 1)
[  250.820273] wlan1: authenticated
[  250.820303] wlan1: associate with AP 00:22:b0:e8:9c:11 (try 1)
[  250.822773] wlan1: RX AssocResp from 00:22:b0:e8:9c:11 (capab=0x411 status=0 aid=2)
[  250.822778] wlan1: associated
[  250.825084] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  251.718112] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[  251.916026] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 2)
[  252.116026] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 3)
[  252.118036] wlan0: direct probe responded
[  252.118040] wlan0: authenticate with AP 00:22:b0:e8:9c:11 (try 1)
[  252.119796] wlan0: authenticated
[  252.119842] wlan0: associate with AP 00:22:b0:e8:9c:11 (try 1)
[  252.122305] wlan0: RX AssocResp from 00:22:b0:e8:9c:11 (capab=0x411 status=0 aid=4)
[  252.122314] wlan0: associated
[  261.732017] wlan1: no IPv6 routers present
[  264.672088] wlan0: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[  347.936129] wlan1: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[  360.132764] wlan1: deauthenticating from 00:23:cd:12:2e:e0 by local choice (reason=3)
[  360.346157] wlan1: direct probe to AP 00:23:cd:12:2e:e0 (try 1)
[  360.351076] wlan1: direct probe responded
[  360.351084] wlan1: authenticate with AP 00:23:cd:12:2e:e0 (try 1)
[  360.352897] wlan1: authenticated
[  360.352928] wlan1: associate with AP 00:23:cd:12:2e:e0 (try 1)
[  360.356091] wlan1: RX AssocResp from 00:23:cd:12:2e:e0 (capab=0x421 status=0 aid=2)
[  360.356101] wlan1: associated
[  449.629030] device wlan1 entered promiscuous mode
[  459.589059] device wlan1 left promiscuous mode
[  497.765042] wlan1: deauthenticating from 00:23:cd:12:2e:e0 by local choice (reason=3)
[  504.937673] wlan1: deauthenticating from 00:23:cd:12:2e:e0 by local choice (reason=3)
[  505.262160] wlan1: direct probe to AP 00:23:cd:12:2e:e0 (try 1)
[  505.275816] wlan1: direct probe responded
[  505.275823] wlan1: authenticate with AP 00:23:cd:12:2e:e0 (try 1)
[  505.288149] wlan1: authenticated
[  505.288189] wlan1: associate with AP 00:23:cd:12:2e:e0 (try 1)
[  505.291173] wlan1: RX AssocResp from 00:23:cd:12:2e:e0 (capab=0x421 status=0 aid=2)
[  505.291178] wlan1: associated
[  567.085045] wlan1: deauthenticating from 00:23:cd:12:2e:e0 by local choice (reason=3)
[  572.671123] wlan0: deauthenticating from 00:22:b0:e8:9c:11 by local choice (reason=3)
[  572.869036] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 1)
[  573.068030] wlan0: direct probe to AP 00:22:b0:e8:9c:11 (try 2)
[  573.070060] wlan0: direct probe responded
[  573.070065] wlan0: authenticate with AP 00:22:b0:e8:9c:11 (try 1)
[  573.071854] wlan0: authenticated
[  573.071902] wlan0: associate with AP 00:22:b0:e8:9c:11 (try 1)
[  573.075592] wlan0: RX AssocResp from 00:22:b0:e8:9c:11 (capab=0x411 status=0 aid=2)
[  573.075597] wlan0: associated
[  595.129031] device wlan0 entered promiscuous mode
[  612.401082] device wlan0 left promiscuous mode

```sudo lshw -C network
 ```
 *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wlan0
       version: 00
       serial: 00:0e:2e:9a:60:e1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=10.0.0.10 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:feaf8000-feafffff
  *-network:1
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 86
       serial: 00:50:fc:b0:f0:96
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:b800(size=256) memory:feaf7c00-feaf7cff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:e0:0c:e0:da:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```iwlist wlan1 scan
```
wlan1     No scan results
```lsb_release -d
```
Description:    Ubuntu 10.04.2 LTS
```uname -mr
```
2.6.32-28-generic i686
```

Same issue here, since Natty.

---

