---
title: "Trying to resume from accessing local IP"
date: 2013-08-04
forum: Networking &amp; Wireless
---

### Post by cowboys4life2 on 2013-08-04
I'm trying to get my Ubuntu minimal server to wake from suspend by typing in 192.168.1.100 from any other computer on the network, and also over the internet at [https://external-IP:sabnzbdport](https://external-IP:sabnzbdport). My Windows 7 PC is capable of doing this and I was hoping that Ubuntu was as well. My Ubuntu server is able to WOL by sending a magic packet but I would just like to be able access the IP and have it resume from suspend. Main reason is if I'm away from my computer I can still download to it and then enjoy it when I return home. Any ideas? I can't seem to figure it out. Just let me know if I can help by running any commands.

ethtool eth0
```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: ug
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes
```

---

