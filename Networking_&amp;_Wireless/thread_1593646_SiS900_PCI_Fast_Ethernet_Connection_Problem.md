---
title: "SiS900 PCI Fast Ethernet Connection Problem"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by tchaikovsky88 on 2010-10-11
Hey,
i just installed ubuntu 10.04 with a new motherboard. All hardware is doing just fine except my integrated lan network device (SiS900) witch doesn't connect to the network.

I had to plug in another pci lan card to access internet, and i could be ok with that solution, but i would like to activate the WOL capabilities of my board so i'm hopping anyone comes up with a solution since it looks to me like an hardware configuration issue.

```

root@xxxx:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:4b:bc:84:55  
          inet addr:192.170.1.149  Bcast:192.170.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:4bff:febc:8455/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4579 errors:0 dropped:0 overruns:0 frame:0
          TX packets:836 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1579204 (1.5 MB)  TX bytes:116019 (116.0 KB)
          Interrupt:17 Base address:0x8f80 

eth1      Link encap:Ethernet  HWaddr 00:0b:6a:a4:20:09  
          inet6 addr: fe80::20b:6aff:fea4:2009/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35537 (35.5 KB)  TX bytes:2862 (2.8 KB)
          Interrupt:19 Base address:0xd400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


```
```


root@scooby:~# dmesg | grep eth0
[    1.108364] eth0: SiS 900 PCI Fast Ethernet at 0xd400, IRQ 19, 00:0b:6a:a4:20:09
[   23.652281] udev: renamed network interface eth1 to eth0
[   23.654006] udev: renamed network interface eth0_rename to eth1
[   25.194570] eth0:  setting full-duplex.
[   35.264059] eth0: no IPv6 routers present

root@scooby:~# dmesg | grep eth1
[   23.652281] udev: renamed network interface eth1 to eth0
[   23.654006] udev: renamed network interface eth0_rename to eth1
[   27.185005] eth1: Media Link On 100mbps full-duplex 
[   35.760051] eth1: no IPv6 routers present


```*Why is udev renaming my devices?

```


root@xxxx:~# ethtool eth0
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 24
    Transceiver: internal
    Auto-negotiation: on
    Current message level: 0x00000001 (1)
    Link detected: yes

root@xxxx:~# ethtool eth1
Settings for eth1:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000c5 (197)
    Link detected: yes


```

---

