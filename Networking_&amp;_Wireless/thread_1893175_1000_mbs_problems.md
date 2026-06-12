---
title: "1000 mb/s problems"
date: 2011-12-09
forum: Networking &amp; Wireless
---

### Post by elliotbeken on 2011-12-09
Hi all,

i have a ubuntu server 11.04 64bit running on a hp microserver. the card in the server can handle a 1gb/s connection but for some reason it only connects at 100 mb/s !

the switch is connects too is a cisco 1gb/s so i would of thought it would auto connect at 1gb/s but it has not!

how do i make it use the correct settings 

Thanks

---

### Post by jonobr on 2011-12-09
Hi

If you use something like ethtool it may show you info on your interface.
It could be due to autonegotation not working between the two devices and requiring your nic to be set.
People expect autonegotation to work but there are devices out there that just doint do it well..

Heres a result from my ethernet interface on a bad laptop showing speeds etc. (there may be better tools out there)

> 
sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
        Link detected: yes
lumpy@jabba:~$


you can also use ethtool to disable autneg 
be careful doing this! recommend further reading before tweaking.


> ethtool -s eth0 duplex half autoneg off &#8211; disables auto-negotiation, enables Half Duplex.
ethtool -s eth1 duplex full speed 1000 autoneg off &#8211; disables auto-negotiation, enables half Duplex and sets up Speed to 1000 Mb/s.



---

### Post by marinara on 2011-12-09
you might be using a 100mb cable

---

### Post by jonobr on 2011-12-09
marinara excellent point,
I always assume this.

Cat 5 cable goes up to 100mbps and cant get to 1000mbps
Cat 5e does 1000mbps

Unless its written on the outside its hard to tell the difference.

Inside the cable uses four pair wires instead of two pair.

If you have cat 5 and want to get new cable, you maybe should miss 5e and go for 6 as it is insulated and has more twists on the cable (the fancy term is a "reduces crosstalk")

---

