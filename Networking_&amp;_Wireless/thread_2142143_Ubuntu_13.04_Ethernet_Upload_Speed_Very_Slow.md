---
title: "Ubuntu 13.04 Ethernet Upload Speed Very Slow"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by peshko-lnx on 2013-05-04
Just installed Ubuntu 13.04 on my Toshiba R840 laptop together with  Windows 7. Installation was a breeze. Everything works fine. Checked the  speed on speedtest.net. Surprisingly my ethernet upload speed is about 4  times slower than the same test done on my Windows 7 and wireless on  Ubuntu. When I take it off the ethernet in Ubuntu and use the wireless,  wireless has a perfect speedtest.

  
Here are the speedtest.net results All to the same test server:

  
Windows 7 Ethernet - Up 83.11/Down 39.21
Ubuntu Wifi - Up 82.37/Down 39.01
Ubuntu Ethernet - Up 83.07/Down 9.02

  
Something is not right.

  
The output of the ethtool:

Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 2
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000007 (7)
                   drv probe link
    Link detected: yes

---

### Post by philipMac on 2013-05-05
Also having huge issues with 13.04 wireless on an Asus Zenbook. It's dramatically worse than 12.10.

---

### Post by varunendra on 2013-05-06
@ peshko-lnx,
Please post output of -
```
lspci -nnk | grep -iA2 net
lsmod
ifconfig
```


@ philipMac,
Since yours is a different problem than OP's, I'd recommend to start your own thread providing the details of the problem.

---

