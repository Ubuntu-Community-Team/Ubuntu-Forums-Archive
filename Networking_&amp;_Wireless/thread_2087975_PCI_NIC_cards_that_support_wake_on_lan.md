---
title: "PCI NIC cards that support wake on lan"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by mattbrowne on 2012-11-25
Hi,

I have recently built an ubunutu box using a dell dimension C521 and I cannot for the life of me get wol to work.

Ethtool looks to be setup correctly:

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
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: g
        Current message level: 0x000000ff (255)
        Link detected: yes

And the nic link and activity light are on when the box is powered off.

But the box will not respond to wol - the bios appears to be setup correctly (although there is no explicit wol config item).

So... I was wondering if there were any PCI NIC card (low profile) that are known to work with ubuntu on wol.

Many thanks!

---

