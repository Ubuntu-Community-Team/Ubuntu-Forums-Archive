---
title: "mii-tool not working"
date: 2006-06-02
forum: Networking &amp; Wireless
---

### Post by wuch on 2006-06-02
Hi,

I just installed a ECS C51G-M754 mobo and a Sempron 64 2800+ processor. I d/l the 64 bit version of Ubuntu and I can't seem to get my network card to work. I'm trying to follow the Wired Ethernet Trouble Process post but when I run:

`sudo mii-tool eth0`

I get the following error:

SIOCGMIIPHY on 'eth0' failed: Operation not supported

Can anyone tell me what I need to do? Am I not supposed to use the 64 bit version of Ubuntu?

Thanks in advance.

---

### Post by Asim_zaka on 2006-08-29
Hi there,

Did you get around the mii-tool problem? I am facing the same errors:

mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found

With the eth0 interface settings:


/usr/local/sbin/ethtool eth0
Settings for eth0:
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
        PHYAD: 24
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000001 (1)
        Link detected: yes

What can I do?

Asim.

---

