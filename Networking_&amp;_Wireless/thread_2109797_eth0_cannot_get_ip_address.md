---
title: "eth0 cannot get ip address"
date: 2013-01-28
forum: Networking &amp; Wireless
---

### Post by ezandi on 2013-01-28
I have an Ubuntu 12.04 desktop with two ethernet cards. I I connect eth0 to the corporate LAN and eth1 to a Lynksys router then both the interfaces get an ip address. However if I connect eth1 to corporate LAN and eth0 to the router, then the eth0 never gets an ipaddress. How can I debug this? In the later case the o/p of ifconfig is 

eth0      Link encap:Ethernet  HWaddr 00:04:76:de:08:67  
          inet6 addr: fe80::204:76ff:fede:867/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:82827 errors:1 dropped:0 overruns:1 frame:1
          TX packets:84472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12041885 (12.0 MB)  TX bytes:42357813 (42.3 MB)
          Interrupt:18 Base address:0xcf80 

eth1      Link encap:Ethernet  HWaddr 00:1e:4f:df:29:64  
          inet addr:128.247.77.0  Bcast:128.247.77.255  Mask:255.255.254.0
          inet6 addr: fe80::21e:4fff:fedf:2964/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1402630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1535695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:212030291 (212.0 MB)  TX bytes:1060491787 (1.0 GB)
          Interrupt:21 Memory:fe9e0000-fea00000 
The setting of my cards are

####:~ $ sudo ethtool eth0
[sudo] password for sachin: 
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 24
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: d
    Current message level: 0x00000001 (1)
                   drv
    Link detected: yes
####:~ $ sudo ethtool eth1
Settings for eth1:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 1
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000001 (1)
                   drv
    Link detected: yes

---

### Post by matt_symes on 2013-01-28
Hi

Try to get an IP address manually.

```
sudo dhclient eth1
```

What output does this command produce ?

Kind regards

---

### Post by ezandi on 2013-01-28
Thanks. Had tried that too. It takes some time before returning and does nothing. That is ifconfig still shows no ipaddress for eth0. I even tried to statically allocate ipaddress to eth0. That works fine for sometime. Thus...

####:~ $ sudo ifconfig eth0 192.168.1.101 netmask 255.255.255.0

####:~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:de:08:67  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::204:76ff:fede:867/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83521 errors:1 dropped:0 overruns:1 frame:1
          TX packets:87286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12274498 (12.2 MB)  TX bytes:43065311 (43.0 MB)
          Interrupt:18 Base address:0xcf80 

eth1      Link encap:Ethernet  HWaddr 00:1e:4f:df:29:64  
          inet addr:128.247.77.0  Bcast:128.247.77.255  Mask:255.255.254.0
          inet6 addr: fe80::21e:4fff:fedf:2964/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1578201 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1763475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:231088720 (231.0 MB)  TX bytes:1291574088 (1.2 GB)
          Interrupt:21 Memory:fe9e0000-fea00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:75749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:75749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7222510 (7.2 MB)  TX bytes:7222510 (7.2 MB)

but after couple of minutes

####:~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:04:76:de:08:67  
          inet6 addr: fe80::204:76ff:fede:867/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:83532 errors:1 dropped:0 overruns:1 frame:1
          TX packets:87382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12278579 (12.2 MB)  TX bytes:43087712 (43.0 MB)
          Interrupt:18 Base address:0xcf80

---

### Post by matt_symes on 2013-01-30
Hi

I don't think this is a dhcp problem but FYI, i should have told use to use the -v switch

```
sudo dhclient -v <interface>
```

This gives debug information. 

I would start tailing a long file next and the try to get an IP address or assign on statically and wait until the ip is lost

```
tail -f /var/log/syslog
```

Start tailing the logfile before you try to get an ip addrress.

Any useful information by doing that ?

Kind regards

---

### Post by SeijiSensei on 2013-01-30
Maybe the corporate DHCP server only responds to known MAC addresses?  Have you asked your company's IT department about this?  It may have nothing to do with your machine at all.

---

