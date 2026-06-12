---
title: "kubuntu showing 2 different nework speeds (wired)"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by skreamz on 2011-09-14
Hi, it seems I can only connect at 10mb which the networking interface is showing but when I type 

ethtool eth0 

it shows the following

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
        Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                             100baseT/Half 100baseT/Full 
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
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

which says I'm connected at 100 mb I'm guessing the network interface is the correct one, as I have tested the speed, how would I set it at least to 100?

thank in advance.

[IMG]http://www.4freeimagehost.com/show.php?i=1296052e12ac.png[/IMG]
[ [img]http://www.4freeimagehost.com/resized/1296052e12ac.png[/img]](http://www.4freeimagehost.com/show.php?i=1296052e12ac.png)


managed to solve this by installing the drivers from the realtek website.

---

