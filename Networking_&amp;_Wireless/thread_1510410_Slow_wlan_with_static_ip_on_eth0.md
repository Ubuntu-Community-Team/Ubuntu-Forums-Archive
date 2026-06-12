---
title: "Slow wlan with static ip on eth0"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by petestaar on 2010-06-15
Hi all.

I have set at static ip on eth0:

In have configured the /etc/network/interfaces as:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.112
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

However, I experience a slow Internet connection when using wlan.

Is this a routing issue, or have I configured the /etc/network/interfaces config file wrong?

I use Ubuntu 10.04, 2.6.32-22-generic

All suggestions are welcome...

Regards 

Peter

---

### Post by Iowan on 2010-06-15
You might check the results of **route -n**, but the gateway address might be a problem for wireless - it would seem to want to send all non-local traffic via eth0.

---

### Post by bigmojo74 on 2010-06-15
Could possibly be your duplex, you can see that info by running the following command - don't need all the output just what you see below - though if you want to post it all that wouln't hurt either. Your /etc/network/interfaces file looks good.

$sudo ethtool eth0
...
Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on

---

