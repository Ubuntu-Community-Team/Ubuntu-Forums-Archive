---
title: "How to Edit wired (ethernet cable) internet (SC92031 NIC)"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by sunshine19 on 2010-08-29
[FONT=Times New Roman][SIZE=2]I have recently install Ubuntu 10.04, i can connect to the Internet but i can't edit wired Ethernet Interface Configuration.  when i config using ethtool and mii-tool i am getting errors as below.
[B]
[COLOR=Red]sunhine@dualpower19:~$ sudo ethtool eth1[/COLOR][/B]
Settings for eth1:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 100baseT/Half 100baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: d
    Link detected: yes
**[COLOR=Red]sunhine@dualpower19:~$ sudo ethtool -s eth1 speed 10 duplex full autoneg off[/COLOR]**
Cannot set new settings: Invalid argument
  not setting speed
  not setting duplex
  not setting autoneg
**[COLOR=Red]sunhine@dualpower19:~$ [/COLOR]**


[SIZE=4]Please solve my problem [/SIZE]
[/SIZE][/FONT]

---

