---
title: "Server 12.04 WAN NIC loses connection"
date: 2012-08-03
forum: Networking &amp; Wireless
---

### Post by bobbydams on 2012-08-03
I am installing a 12.04 server which has dual NICs with a static private and static public IP. For some reason the public IP is accessible for about 10 minutes and then the connection drops. When I log into the server and do an arp-scan eth0, then suddenly I can reach it from the public IP again. The WAN is behind a firewall. The syslog doesn't show anything out of the ordinary. Is there anything I can check within the server NIC settings?

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
        Advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: off
        MDI-X: Unknown
        Supports Wake-on: umbg
        Wake-on: d
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes
```

---

