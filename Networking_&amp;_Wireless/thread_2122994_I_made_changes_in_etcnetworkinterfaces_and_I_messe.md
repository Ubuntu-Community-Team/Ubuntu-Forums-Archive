---
title: "I made changes in /etc/network/interfaces and I messed it up"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by poinu on 2013-03-06
Hello,

All started when I tried to configurate "wake on lan" on my Ubuntu Server 12.10 x64. I downloaded 'wakeonlan' and 'ethtool' and after I had my BIOS configurated and had ran 'sudo ethtool -s eth0 wol g' everything worked like a charm. Then I thought I'd have been nice to automatize it so I could forget about running 'sudo ethtool -s eth0 wol g' at each boot so I looked up some information. 

I found out that that networking parameters could be configured in /etc/network/interfaces so I went for it, the file looked like this back then:
```

# This file describes the network interfaces available on your system# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp
post-up /sbin/ethtool -s wol g
post-down /sbin/ethtool -s wol g

```

I didn't realise those commands where incorrect and then I saved and I rebooted the server to check the results. From here on, everything went from bad to worse. When the server was booting (still at each boot now) it took far longer than normal and I got error messages telling me something like 'Waiting for network configuration...'. When I logged in the server I realised I had no internet connection, then I restored the /etc/network/interfaces as it was before the crash but, after restarting again, I realised this problem was not only for the server but also for the rest of OS installed including a Ubuntu 12.10 x64 and even a Windows.

It really seems hardware related so I looked for 'ethtool' commands for resetting my network's card configuration but after trying many things, I could not have it working yet. As the whole machine had no connection to Internet I borrowed a wifi card from a friend but I really need to get this working soon, otherwise I won't be able to continue on my projects :S

I really hope someone can give me the ultimate solution to this :)

Additional info:

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 14:da:e9:df:31:a6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1769 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:207530 (207.5 KB)  TX bytes:207530 (207.5 KB)


wlan0     Link encap:Ethernet  HWaddr f8:d1:11:89:5c:9d  
          inet addr:192.168.1.135  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::fad1:11ff:fe89:5c9d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16546 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14674 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13175365 (13.1 MB)  TX bytes:2599400 (2.5 MB)

```

sudo ethtool eth0:
```

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: Unknown!
    Duplex: Unknown! (255)
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x0000003f (63)
                   drv probe link timer ifdown ifup
    Link detected: no

```

sudo lshw -class network:
```

  *-network               
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 14:da:e9:df:31:a6
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI latency=0 link=no multicast=yes port=twisted pair
       resources: irq:49 memory:fe9c0000-fe9fffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: AR5416 Wireless Network Adapter [AR5008 802.11(a)bgn]
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:04:01.0
       logical name: wlan0
       version: 01
       serial: f8:d1:11:89:5c:9d
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-25-generic firmware=N/A ip=192.168.1.135 latency=168 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:febf0000-febfffff

```

cat /var/run/network/ifstate:
```

lo=lo

```

---

