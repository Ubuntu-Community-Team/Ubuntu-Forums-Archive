---
title: "eth0 port speed 100Mbps, duplex half ; how to change it to full?"
date: 2013-06-05
forum: Networking &amp; Wireless
---

### Post by trojanworrier on 2013-06-05
Hi, 

eth0 port speed 100Mbps, duplex half ; how to change it to full? I followed directions shown in following link but still no luck:

[http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-ethernet-network-card-speed-and-duplex-settings-in-ubuntu.html)

---

### Post by Doug S on 2013-06-05
Is full duplex one of the options for that network interface? Example:```
doug@test-smy:~$ [COLOR=#ff0000]sudo ethtool eth0[/COLOR]
Settings for eth0:
        Supported ports: [ TP MII ]
        [COLOR=#ff0000]Supported link modes[/COLOR]:   10baseT/Half 10baseT/Full
                                100baseT/Half [COLOR=#ff0000]100baseT/Full[/COLOR]
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        [COLOR=#ff0000]Advertised link modes[/COLOR]:  10baseT/Half 10baseT/Full
                                100baseT/Half [COLOR=#ff0000]100baseT/Full[/COLOR]
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
        Link partner advertised pause frame use: Symmetric
        Link partner advertised auto-negotiation: Yes
        [COLOR=#ff0000]Speed: 100Mb/s
        Duplex: Full[/COLOR]
        Port: MII
        PHYAD: 32
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: d
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes
```

---

