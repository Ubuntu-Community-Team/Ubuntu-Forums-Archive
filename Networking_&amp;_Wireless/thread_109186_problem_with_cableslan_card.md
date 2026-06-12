---
title: "problem with cables/lan card"
date: 2005-12-28
forum: Networking &amp; Wireless
---

### Post by php4us on 2005-12-28
Hi,

One machine that was previously using Win XP have no problem with the LAN using a cat5 cable.  When we used Kubuntu on the same machine, everything worked fine except the cable. Notice I did not say, the LAN card, because in our testing, when we use a different cable, it works ok.  Just this cable that is formerly being used by the same machine. There's no problem with the cable -- the card is lighting when we are plugging it in.  (You may say, why don't you just use the cable that's currently working? There are other factors that we are considering like the existing cabling of the room, etc.)

Now, I remember something that we did with this formerly XP machine. We are able to set in the network card configuration something like auto, 10/100 or 10/10.  When we were playing around these configurations, one of these worked.  The problem is, i can't find any configuration settings like that with Kubuntu. Can you help me out finding out any linux equivalent of htis?

---

### Post by cylon359 on 2005-12-28
?

Just because the light comes on, doesn't mean the cable works.  I have one that only works at 10 Mbps, but the light comes on in 100 Mbps mode.

You can try to force it to 10 Mbps mode using mii-tool

---

### Post by mips on 2005-12-28
I would really recommend replacing the cable and running at 100Mb/s Ful-Duplex. You already determined the cable is a problem so why stick with it if it is causing problems ?

You can try mii-tool or ethtool.

**_mii-tool:_**
Options are- 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
**sudo mii-tool -F 100baseTx-FD eth0** would set the card to 100Mb/s Full-Duplex

**_ethtool:_**
Options are-
-s DEVNAME \
                [ speed 10|100|1000 ] \
                [ duplex half|full ]    \
                [ port tp|aui|bnc|mii|fibre ] \
                [ autoneg on|off ] \
                [ phyad %d ] \
                [ xcvr internal|external ] \
                [ wol p|u|m|b|a|g|s|d... ] \
                [ sopass %x:%x:%x:%x:%x:%x ] \
                [ msglvl %d ]
[B]sudo ethtool -s eth0 speed 100
sudo ethtool -s eth0 duplex full[/B]

---

