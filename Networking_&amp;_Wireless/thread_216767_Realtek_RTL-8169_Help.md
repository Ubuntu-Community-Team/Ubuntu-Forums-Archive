---
title: "Realtek RTL-8169 Help"
date: 2006-07-16
forum: Networking &amp; Wireless
---

### Post by antilog on 2006-07-16
I am trying to setup an Ubuntu box as a NAT/Firewall w/ wireless using:

Ubuntu 6.06
Firestarter

eth0 - 0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller  (rev a1)

eth1 - 0000:01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigab it Ethernet (rev 10)

ath0 - 0000:01:07.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

eth0 - internet - connected to cable modem
eth1 - local - connected to gigabit switch
ath0 - wireless, haven't setup yet

eth0 is connecting and getting an IP, able to browse internet OK.
I am unable to connect to the network with eth1, and unable to change negotiation settings.

```
 sudo ethtool eth1
Settings for eth1:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x00000033 (51)
        Link detected: no

```

```
 ifconfig eth1
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:x.x.x.x Bcast:x.x.x.x  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967268 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:217

```

where x.x.x.x is a local address I set.

I've read and read and read, and have spent hours trying to get this to work - does anyone have any ideas? From what I am reading I should probably just buy a different card.

Thanks

---

### Post by antilog on 2006-07-16
If I can't get this working, what gigabit card works well with Ubuntu?

Thanks

---

### Post by antilog on 2006-07-17
Bump!

---

### Post by antilog on 2006-07-18
I ditched the Realtek card and am using a 3Com 3c905c 100Mb card which is working great.

---

