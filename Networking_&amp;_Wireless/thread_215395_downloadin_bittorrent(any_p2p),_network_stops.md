---
title: "downloadin bittorrent(any p2p), network stops"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by drainman on 2006-07-13
I am very new to linux so i wont even pretend to now much :I

the problem is starts when i downloaded (from bittorent, amule, even using samba or icq. not ftp, http, synaptics though) for about 10 seconds then my network sudenly stops everything. i have no clue why, the only thing i know is that it is very frustrating.

I really dont know what u guys need to understand what might cause this problem but this i know:

I got a LG LW70 and a router dlink Di-704P and a adsl modem.
my ifconfig eth0:

eth0      Link encap:Ethernet  HWaddr 00:E0:91:0B:35:6D
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:91ff:fe0b:356d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4944 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7213484 (6.8 MiB)  TX bytes:688731 (672.5 KiB)
          Interrupt:169


this is something dont know if it helps though :P :

lspci | grep -i ethernet
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 10)

something else ;) :

ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Current message level: 0x000000ff (255)
        Link detected: yes


I dont have anything else just tell me what u need to (hopefully) solve this problem

Hopefull Jonas

---

### Post by drainman on 2006-07-14
I got this friend that tells me that i might fix this if i build a new kernel ](*,). do anyone know if this is going to help me? 

do anyone know a good site on how to do it?

it sounds like a bit to much challange for a newb like me what do you say?

---

