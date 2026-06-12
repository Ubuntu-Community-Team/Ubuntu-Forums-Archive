---
title: "Ubuntu 10 connection speed"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by tyler.krehbiel on 2010-11-12
Hey All,

New poster, but I have used the threads countless times when searching for help!

Anyway, I am trying to figure out how to view my network connection speed. EG: 10/100/100 mbit.

I searched and searched with no luck, I tried ethtool as well as mii-tool.

Any ideas?

---

### Post by grahammechanical on 2010-11-12
If you are not using a dial-up modem you can log on to the setup program of the modem using a web browser. You put the router address in the web browser just like any web page address. The information in the router set up program should give the upload and download speeds. At the moment my upload speed is 448 kbps. Whereas , 8,128 kbps is the download speed.

Regards

---

### Post by tyler.krehbiel on 2010-11-12
Huh?

I just want to see what speed my network card is connected. Ya know like 100 Mbps or 10 Mbps or 1000 Mbps.

Nothing to do with a modem or download speeds or upload speeds....

---

### Post by uncaspi on 2010-11-12
Choose <System> < Administration> <System monitor> Tab Resources

---

### Post by bottomless on 2011-02-03
@tyler.krehbiel

Use ethtool and not mii-tool.

mii-tool is deprecated and doesn't support gigabit Ethernet.

Popup a shell console and type: /sbin/ethtool eth0 and you'll see your speed:

```

bash# /sbin/ethtool eth0
Settings for eth0:
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
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: umbg
        Wake-on: g
        Current message level: 0x00000003 (3)
        Link detected: yes
bash#

```

You can see the line above: Speed: 1000Mb/s

check there for more info:
[http://blog.bottomlessinc.com/2011/02/using-ethtool-to-determine-ethernet-link-speed-not-mii-tool/](http://blog.bottomlessinc.com/2011/02/using-ethtool-to-determine-ethernet-link-speed-not-mii-tool/)

I wonder why Ubuntu still ships mii-tool

---

