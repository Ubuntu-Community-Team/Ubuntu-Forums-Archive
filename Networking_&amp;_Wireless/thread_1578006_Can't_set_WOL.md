---
title: "Can't set WOL"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by thomellis on 2010-09-19
I'm trying to setup WOL for my server, but I'm getting an error.   Here are the ethtool stats:

> sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: external
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Link detected: yes


So I know its supported, so I try the following command, which produces the error:

> sudo ethtool -s eth0 wol d
Cannot set new wake-on-lan settings: Operation not supported
  not setting wol

Some more info:

> sudo ethtool -i eth0
driver: uli526x
version: 0.9.3
firmware-version:
bus-info: 0000:00:11.0

~$ cat /proc/version
Linux version 2.6.31-14-server (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009


Any ideas??  Let me know if there is more info I can provide.  Thanks in advance.

---

