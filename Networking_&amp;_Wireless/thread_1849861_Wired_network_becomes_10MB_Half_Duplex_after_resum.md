---
title: "Wired network becomes 10MB Half Duplex after resume from suspend"
date: 2011-09-25
forum: Networking &amp; Wireless
---

### Post by mac666 on 2011-09-25
Hello,
I really need help with this one;
I have wired 100 MB from my ubuntu 10.04 with kernel 2.6.32-33-generic.
After i suspend the system and then wake the system, 
Eth0 becomes 10MB half duplex. 
dmesg doesnt tell me much:

[  112.796601] r8169: eth0: link up
[  112.797941] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  123.130022] eth0: no IPv6 routers present
[  182.507840] r8169: eth0: link down
[  185.050564] r8169: eth0: link up

```

dj@diskoteket:~$ sudo ethtool eth0
[sudo] password for dj:
Settings for eth0:
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
dj@diskoteket:~$ sudo pm-suspend
dj@diskoteket:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  Not reported
        Advertised pause frame use: No
        Advertised auto-negotiation: No
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: 10Mb/s
        Duplex: Half
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: off
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
dj@diskoteket:~$


```

If reboot the system, the network works just fine. 
Anyone? Please! 
Thank you

---

### Post by mac666 on 2011-09-26
Shamless bump

---

### Post by mac666 on 2011-09-27
I fixed this by installing correct drivers for my realtek RTL8101E/RTL8102E card.
Google It! :-)

---

