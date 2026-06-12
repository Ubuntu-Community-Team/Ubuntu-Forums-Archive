---
title: "Wired and Wireless Connections Not Working on Two Installs after Normal Update"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by rstromberg on 2011-10-30
*The Problem*
Neither of two Ubuntu systems will connect to wired or wireless network connection. Both went offline at the same time. Both were connecting fine previously. It seems that the problem arose after updating via Update Manager.

*My Two Systems*
1. Ubuntu 10.04 (installed alone, recently)
2. Ubuntu 11.10 (dual install w/ Win7, upgraded from 10.04 > 11.04 > 11.10)

*Symptoms*
a. The router **is** seen by both systems.
b. iwconfig shows "no wireless extensions" at **lo** or **eth0**, but it sees the card and the router at **wlan0**.
c. Network Connections does not include wlan0 or eth0 under wired connections. Only includes **Auto Ethernet**.
d. Connections indicator in menu bar shows trying to connect upon start-up with no success. When clicking to connect on **Auto Ethernet** (wired) or **MY_ROUTER** (wireless), also no success.
e. The driver is present: via-rhine
f. Neither Ubuntu PC can access the internet via Firefox nor Chromium.
g. I have an internet connection on my Win7 install (same PC as 2. above). 

*Thank You*
How should I proceed? My internet disappeared and I want it back.

---

### Post by rstromberg on 2011-10-30
For the specs and problem terminal outputs, I will focus on the recent 10.04 install
(although the problem is present on both Ubuntu install systems).

*1) Machine Brand*
A PC I built several years ago.

*2) Network Wireless Card*
VT6102 [Rhine-II], VIA Technologies

*3) ifconfig*
```
eth0      Link encap:Ethernet  HWaddr 00:0c:6e:1b:af:23 
          inet6 addr: fe80::20c:6eff:fe1b:af23/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:14040 (14.0 KB)  TX bytes:1836 (1.8 KB)
          Interrupt:23 Base address:0xc000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0d:08:40:03:de 
          inet6 addr: fe80::20d:8ff:fe40:3de/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:8190 (8.1 KB)
```*4) iwconfig*
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"\x05\xEF\xF7\x00\xE9\xA1:\xE5\xCA\x0B\xCB\xD0HGd\xBD\x1F#\x1E\xA8\x1C{d\xC5\x14sZ\xC5^Kyc" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated  
          Tx-Power=10 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```*5) lsmod*
```
via_rhine    19154    0
```*6) dmesg*
```
[   16.768609] rt61pci 0000:00:0c.0: firmware: requesting rt2561s.bin
[   16.792886] type=1505 audit(1319976306.008:11):  operation="profile_load" pid=738 name="/usr/bin/evince-thumbnailer"
[   16.833945] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.847418] eth0: link up, 10Mbps, half-duplex, lpa 0x0020
[   16.921356] ICE1712 0000:00:0d.0: enabling device (0004 -> 0005)
[   16.921373] ICE1712 0000:00:0d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   17.094266]   alloc irq_desc for 22 on node -1
[   17.094273]   alloc kstat_irqs on node -1
[   17.094287] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   17.096469] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   17.616225] codec_read: codec 0 is not valid [0xfe0000]
[   17.625915] codec_read: codec 0 is not valid [0xfe0000]
[   17.637379] codec_read: codec 0 is not valid [0xfe0000]
[   17.650156] codec_read: codec 0 is not valid [0xfe0000]
[   24.534669] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[   24.534831] wlan0: direct probe to AP e0:46:9a:64:59:a2 (try 1)
[   24.538694] wlan0: direct probe responded
[   24.538709] wlan0: authenticate with AP e0:46:9a:64:59:a2 (try 1)
[   24.540497] wlan0: authenticated
[   24.540551] wlan0: associate with AP e0:46:9a:64:59:a2 (try 1)
[   24.542986] wlan0: RX AssocResp from e0:46:9a:64:59:a2 (capab=0x411 status=0 aid=1)
[   24.542995] wlan0: associated
[   24.543878] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   27.708011] eth0: no IPv6 routers present
[   35.336034] wlan0: no IPv6 routers present
[   70.007753] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[   70.196572] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[   70.396078] wlan0: direct probe to AP e0:46:9a:64:59:a2 (try 1)
[   70.399035] wlan0: direct probe responded
[   70.399042] wlan0: authenticate with AP e0:46:9a:64:59:a2 (try 1)
[   70.400766] wlan0: authenticated
[   70.400803] wlan0: associate with AP e0:46:9a:64:59:a2 (try 1)
[   70.403170] wlan0: RX AssocResp from e0:46:9a:64:59:a2 (capab=0x411 status=0 aid=1)
[   70.403175] wlan0: associated
[  116.001226] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[  116.194075] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[  116.392075] wlan0: direct probe to AP e0:46:9a:64:59:a2 (try 1)
[  116.395027] wlan0: direct probe responded
[  116.395033] wlan0: authenticate with AP e0:46:9a:64:59:a2 (try 1)
[  116.396743] wlan0: authenticated
[  116.396779] wlan0: associate with AP e0:46:9a:64:59:a2 (try 1)
[  116.399110] wlan0: RX AssocResp from e0:46:9a:64:59:a2 (capab=0x411 status=0 aid=1)
[  116.399115] wlan0: associated
[  161.997994] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[  162.190056] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[  162.388078] wlan0: direct probe to AP e0:46:9a:64:59:a2 (try 1)
[  162.391029] wlan0: direct probe responded
[  162.391035] wlan0: authenticate with AP e0:46:9a:64:59:a2 (try 1)
[  162.392784] wlan0: authenticated
[  162.392830] wlan0: associate with AP e0:46:9a:64:59:a2 (try 1)
[  162.395133] wlan0: RX AssocResp from e0:46:9a:64:59:a2 (capab=0x411 status=0 aid=1)
[  162.395138] wlan0: associated
[  207.996736] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[  208.190002] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
[  208.388079] wlan0: direct probe to AP e0:46:9a:64:59:a2 (try 1)
[  208.391030] wlan0: direct probe responded
[  208.391036] wlan0: authenticate with AP e0:46:9a:64:59:a2 (try 1)
[  208.392745] wlan0: authenticated
[  208.392781] wlan0: associate with AP e0:46:9a:64:59:a2 (try 1)
[  208.395093] wlan0: RX AssocResp from e0:46:9a:64:59:a2 (capab=0x411 status=0 aid=1)
[  208.395097] wlan0: associated
[  253.990644] wlan0: deauthenticating from e0:46:9a:64:59:a2 by local choice (reason=3)
```*7) sudo lshw -C network*
```
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: c
       bus info: pci@0000:00:0c.0
       logical name: wlan0
       version: 00
       serial: 00:0d:08:40:03:de
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:eb800000-eb807fff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0c:6e:1b:af:23
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:23 ioport:9400(size=256) memory:ea800000-ea8000ff
```[I]
8) iwlist scan[/I]
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results
```*9) uname -mr*
```
2.6.32-34-generic i686
```*10) sudo /etc/init.d/networking restart*
```
* Reconfiguring network interfaces...   
USER@MACHINE:~$

```

---

