---
title: "link speed in home network setup"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by taopublic on 2011-04-30
I have two computers. The both connect to a gigabit switch. The switch is connected to a router which runs at 100mb/s. The router is also the DHCP server in my home network.  After the computers boot up, they first talk with the router to get IP etc. So they auto-negotiate at 100MB/s speed.

```

$ sudo ethtool eth0
[sudo] password for tao: 
Settings for eth0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    [B]Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full [/B]
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: Yes
    **Speed: 100Mb/s**
    Duplex: Full

```

Now, is there a way to make the two computers to transmit data between themselves at gigabit speed? My test shows they top out at 93mbps.

---

