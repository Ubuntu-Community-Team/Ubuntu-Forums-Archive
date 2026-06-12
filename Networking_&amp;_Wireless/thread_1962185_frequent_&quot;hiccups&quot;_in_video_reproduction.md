---
title: "frequent &quot;hiccups&quot; in video reproduction over network, samba shares"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by hlb on 2012-04-20
hi everyone,

I'm experiencing the problem mentioned in the subject on several installations of 12.04, 

* both 64 and 32 bit, 

* both with wired and wireless connections,

* with different media players (e.g. movie player and  mplayer2 with high cache and cache-min parameters)

* both with gvfs-fuse-deamon or without - with straight "sambamount" (smbfs) approach


I'd like to dig out the problem with your help.


On the other end, I've both a d-link nas (armel linux, standard firmware) and a regular intel netbook acting as a small file server)

I **don't** experience the problem under windows, mediaplayer-classic, on any of the machines, therefore we can rule out the "cabling and router" possibility.

The bitrate seem quite relevant: 

mplayer2 complains about the cache not filling, and the occurrence is lower on "lightweight" files, while - for example - the rather bitrate-heavy opening of Kara No Kyoukai I, or the subway scene at the beginning of Blood The Last Vampire stutter quite a bit (nm the anime preference, it's only to mention a couple of actual cases).

Encoding seems to not matter.

At the end of this post you'll find an ethtool dump of one of the various tested interfaces; I don't think that the hardware "per-se" is imporant, but I've experienced the problem with a ralink 2500 wireless usb adapter, with an on-board marvell adapter (e8400 processor), and with the standard intel thing on a Z68/core i5 2500k board. On a ION netbook, too.

Copying the content on the local hard disk completely circumvent the problem (but it's not a viable workaround, of course).

what is happening?


thanks a lot




```

root@xpc:~# ethtool eth0
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000ff (255)
                   drv probe link timer ifdown ifup rx_err tx_err
    Link detected: yes
root@xpc:~#
```

---

