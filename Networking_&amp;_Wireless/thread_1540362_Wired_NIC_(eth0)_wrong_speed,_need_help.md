---
title: "Wired NIC (eth0) wrong speed, need help"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by waffletten on 2010-07-27
Tried everything I can find on forums and lost.  I have 3 ubuntu machine on my network (9.10) and two work fine (100Mb/s).  My acer aspire revo R3610 only gets a NIC speed of 10Mb/s.  I have tried manually setting the speeds, different cables, and am a loss.  Any ideas?

My info (from sudo ethtool eth0, sudo lshw -C Network, and ifconfig) ps removed mac address

```
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 10Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: d
    Link detected: yes
*-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:22:68:69:5d:5a
       size: 10MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=10MB/s
       resources: irq:23 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:56:1f:bc:3f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:febf0000-febfffff


eth0      Link encap:Ethernet  HWaddr xxxx 
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:68ff:fe69:5d5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3052 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2933903 (2.9 MB)  TX bytes:550791 (550.7 KB)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr xxxx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr xxxxx
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```I tried to change manually with ethtool but the only setting that works is:
```
sudo ethtool -s eth0 speed 10 duplex full autoneg on
```These don't and I lose my connection:
```
sudo ethtool -s eth0 speed 100 duplex full autoneg on
sudo ethtool -s eth0 speed 1000 duplex full autoneg on
```Do I need to enable a different driver?  Am I missing something? I see lots of errors in the ifconfig results, what's going on?

Any help would be most appreciated.

---

### Post by waffletten on 2010-07-29
I was trying a new Trendnet Gigabit switch when the problems started.  Went back to my linksys switch and all is good.

---

