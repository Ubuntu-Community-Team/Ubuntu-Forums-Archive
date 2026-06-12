---
title: "problems installing new network interface - dhcp ok but no active connection"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by gobbledigook on 2009-05-16
Hi, i am running ubuntu 9.01 as a file server at home, i recently got a gigabit router and soon realised that my servers onboard eth was not gigabit, d'oh!

so i have got a gigabit eth adapter, pci slot one and plugged it in, rebooted, and added it to my /etc/network/interfaces file as follows remembering to restart network after:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.120
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

#The secondary network interface (10/100/1000)
auto eth3
iface eth3 inet dhcp

```

now when i hot-swap the ethernet cable it does dhcp to my router, the MAC is assigned an ip in the dhcp table. However it does not appear in the 'active clients' list and i am not able to connect to it via ssh or samba nor does it respond to pings.

anyone have any ideas? below is some more info specific to the eth3 device:

```

sudo ethtool eth3
Settings for eth3:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: no

```

thanks, 

Dan

---

