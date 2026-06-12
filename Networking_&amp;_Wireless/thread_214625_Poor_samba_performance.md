---
title: "Poor samba performance"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by Tweek84 on 2006-07-12
In the last few days I seem to have developed a problem with my local area network. The performance is just shy of piss poor when attempting to transfer files from a samba share.

There seems to be an artificial limit being imposed when doing transfers from a samba share. I will hit 12 megabits per second and  sit there as if it has hit a wall.

I can then initiate a second transfer and get 22 megabits per second on the two combined transfers so it's clearly not a hardware or performance limitation of any of the hardware involved.

This is a network between kubuntu install of Dapper, and Windows XP Sp1. There is a netgear router in the middle.

There is no packet loss:
> PING compy2600 (172.16.0.105) 56(84) bytes of data.

--- compy2600 ping statistics ---
91317 packets transmitted, 91317 received, 0% packet loss, time 38372ms
rtt min/avg/max/mdev = 0.083/0.113/5.069/0.091 ms, pipe 2, ipg/ewma 0.420/0.108 ms


And here are the results of ethtool eth0

> Settings for eth0:
        Supported ports: [ TP MII ]
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
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pg
        Wake-on: d
        Current message level: 0x000000c5 (197)
        Link detected: yes


That was all I really thought to start with.
Thanks

---

### Post by Tweek84 on 2006-07-12
I also ran a speed test using netcps:

> D:\>NetCPS.exe -m500 lappy2200
NetCPS 1.0 - Entering client mode. Press ^C to quit
Connecting to 172.16.0.110 port 4455... Connected!
---> CPS   7393280.00  KPS:  7220.00  MPS: 7.05
Avrg CPS   8363450.50  KPS:  8167.43  MPS: 7.98
Peek CPS   9090048.00  KPS:  8877.00  MPS: 8.67
Done. 524288000 Kb transferred in 62.70 seconds.

So the link pulled in around 72-75 megabits per second. I know definitely it isn't the hardware.

---

