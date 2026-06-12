---
title: "Gigabit network card started dropping to 100mbit"
date: 2013-03-22
forum: Networking &amp; Wireless
---

### Post by atconc on 2013-03-22
The D-Link DGE-528T card in my PC running ubuntu server 10.04 has recently started only connecting at 100mbit instead of 1gbit.  I've recently had some problems with this box that caused an very aggressive shutdown (badly fitted heatsink triggered an overheat threshold somewhere), but I'm not 100% sure this started at the same time.

I've plugged into another cable, on another port, that is working fine a 1gbit on a different PC and the same happens, so I'm fairly happy it's not a cable issue or hardware issue on the router (Asus RT-N66U)  I've also tried connecting direct to a gigabit switch and had the same problem there as well.  So I think either the card is dieing or something got messed up when the PC didn't shut down properly.  Before I go and order a new card I'm wondering if there's anything I can do to troubleshoot the software side of things first.

```
aaron@triad:~$ sudo ethtool eth1
[sudo] password for aaron:
Settings for eth1:
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
        Link detected: yes

```

Ethtool seems to know it's a gigabit card and suggests the other end isn't offering gigabit, but the same happens with both the router and the switch with cables that are fine on a different pc

lsmod shows 
r8169                  39714  0

Which i think is the correct driver

is there anything else I can try or shall i just buy a new network card?

---

### Post by atconc on 2013-03-23
replacement £10 gigabit PCI card seems to have cured the issue so I guess the old one is trashed

---

