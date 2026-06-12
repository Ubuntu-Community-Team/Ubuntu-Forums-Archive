---
title: "Slow download speeds"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by saga915 on 2010-08-27
Hey all,

I've been using Ubuntu for a while (though I would not consider myself an "expert") and have just gone back to school.  I live on campus and connect to the network through an ethernet cord.

On Windows, the download speed is 1 Mb/s by default, but if you go through and configure the network card (turning off the auto-negotiation and setting the speed to 10, duplex full) the download speed will increase to 10 Mb/s, a considerable difference.

So, I tried to do this in Ubuntu by opening the terminal and typing the following:

sudo ethtool -s eth0 autoneg off speed 10 duplex full

and all of a sudden, my computer isn't connecting to the internet.  When I type:

sudo ethtool -s eth0 autoneg on

it suddenly starts working again.

Does anyone know what I might be able to do to fix this problem?

---

### Post by grahammechanical on 2010-08-27
I am not an expert either, but have you tried the network manager to edit connections? I am guessing, do not take my word for it, but change the MTU might be what you are trying to do. Mine is set to automatic but it can be changed. It goes from 1 to 10,000 bytes. Do not confuse Bytes with bits. Mb/s is Mega bits (I think).  Sorry if I am wrong.

Regards.

---

### Post by BkkBonanza on 2010-08-27
MTU is unrelated. It controls the max size of packets sent on the network and shouldn't be larger than 1500 (unless you have hardware that can use jumbo packets).

I don't have an answer for your ethtool problem. Just about always auto-negotiate should give you the highest speed. Have you just done **sudo ethtool eth0** to see what settings you get by default?

I always get 1000Mbps and full duplex anyway.

---

### Post by saga915 on 2010-08-29
I don't know why, but at my school, the download speed is dramatically different when you switch the settings to Speed 10Mb/s Duplex Full (on both Windows and Mac).  On a previous installation of Ubuntu, this setting also worked.  Now, every combination of different speeds and duplexes kills my internet... Only with autoneg on will it connect.

Here's what the output is when I type sudo ethtool eth0, if that helps:

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  Not reported
    Link partner advertised pause frame use: No
    Link partner advertised auto-negotiation: No
    Speed: 10Mb/s
    Duplex: Half
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: yes

---

### Post by BkkBonanza on 2010-08-30
If you disable auto-neg and the other end doesn't support the mode you try to force it to, then they won't talk. The purpose of auto-neg is to negotiate the highest speed both ends support, and that data is reliably carried. Long or damaged cabling can severly disrupt transmission and prevent a link from working at higher speeds. Sometimes even a severe kink/bend in the cable can affect performance. There are many variables besides just setting the IF mode.

---

