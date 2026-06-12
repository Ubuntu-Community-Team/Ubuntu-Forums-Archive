---
title: "slow gigabit ethernet?"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by RoosterHam on 2013-03-20
I have had this issue before.

I have a desktop that has a FastEthernet NIC and a GigabitEthernet NIC, a server with two Gigabit NICs, and both connect to a Netgear domestic modem/wifi-router/wired-switch via eth0. Transferring files via the 100Mbps switch ports I get 1.5MB/sec transfer via scp/sshfs which is very slow for over 400GB of transfer.

So I patch between eth1 (gigabit nics) and set routes on both hosts to use eth1 for the unique subnet. This has bumped the transfers to 1.7MB/sec.

I have done this once before and had a similar issue. Back then, the hosts were negotiating to half-duplex, and I had to add a pre-up ethtool statement on both hosts to force full-duplex. When I did that, there was a significant increase.

This time ethtool on both hosts report a Speed: 1000Mbps and Duplex: Full. I'm still getting only a slight increase over 100Mbps.

Ethtool eth1 on desktop:
```

Settings for eth1:
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
    Link partner advertised pause frame use: Symmetric
    Link partner advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes

```

Ethtool eth1 on server:
```

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
    MDI-X: Unknown
    Supports Wake-on: d
    Wake-on: d
    Link detected: yes

```

---

