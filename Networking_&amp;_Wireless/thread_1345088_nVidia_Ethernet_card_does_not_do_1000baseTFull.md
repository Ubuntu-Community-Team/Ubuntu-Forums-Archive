---
title: "nVidia Ethernet card does not do 1000baseT/Full"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by Bart-PE on 2009-12-03
Hi all,

I have a Nvidia Ethernet card in my ubuntu 8.10 server.
Connected to an 8-port linksys network switch.
This switch is a gigabyte switch.
All work fine at 100mbit/sec.
But I cannot force the nvidia adapter into 1000baseT/Full mode.

Tried several ethtool options and so.
Still stuck at 100Mb/s

Below is some info.

Does anyone know a solution for this?

Regards,
Bart.

$ lshw
...
description: Ethernet interface
          product: MCP61 Ethernet
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          logical name: eth0
          version: a2
          serial: 00:22:15:ce:cb:6e
          size: 100000000
          capacity: 1000000000
          width: 32 bits
          clock: 66MHz
          capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.178.11 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
...


$ ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
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
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

---

### Post by dmfrey on 2009-12-04
i am having this issue as well on mythbuntu karmic.  Please let me know if you find anything out on this issue.  I will do some digging as well.  I only seem to get a 100 mbit connection.

---

### Post by Bart-PE on 2009-12-07
Hi,

I've seen others do "ethtool -s eth0 speed 1000 advertise 0x20" to fix the speed after suspend/hibernation.

Tried it, but it does not work for me...

Regards,
Bart.

---

### Post by dmfrey on 2009-12-08
That's interesting, i will give it a try tonight.

I did some looking and the nforce boards should just be using forcedeth.  This is the module that's loaded on my box.

Thanks.

---

### Post by dmfrey on 2009-12-08
i found this one too:
```

ethtool eth0

```

it should tell you what speed the port is running at.

I can tell from my router that it is not running at 1000gb, because it would turn orange when it is.  Another box on my network is running at 1000 because it is orange, plus the manual confirms it.

I hope these commands help.  I think also grepping dmesg will help to identify what it thinks  is going on at start up.

---

### Post by covert on 2010-03-29
Anyone have any luck with this. I also have the same problem with the same MCP61 ethernet. 

ethtool -s eth0 speed 1000 advertise 0x20 did not work for me ether.

---

