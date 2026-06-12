---
title: "mii-tool gives error while ethtool shows results"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by raghaven.kumar on 2010-08-31
Hi,

I have upgraded to 10.04 from 9.10 after that, i get this strange issue.
I have acutally asingned static address in the network manager applet.
```
mahiti@mahiti-admin:~$ sudo mii-tool -vv eth4
Using SIOCGMIIPHY=0x8947
SIOCGMIIPHY on 'eth4' failed: Operation not supported
mahiti@mahiti-admin:~$ sudo ethtool  eth4
Settings for eth4:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  Not reported
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: No
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes
mahiti@mahiti-admin:~$
```
If i do ifup also, i get error
```
mahiti@mahiti-admin:~$ sudo ifup eth4
Ignoring unknown interface eth4=eth4.
```
Note: I do have the connection working !

---

### Post by chili555 on 2010-08-31
Is the behavior improved if you use:```
sudo ifconfig eth4 up
```According to *man ifup*, it controls interfaces listed in /etc/network/interfaces. If you configured a static address in Network Manager (a bit of an oxymoron, in my opinion), then eth4 is not listed in /etc/network/interfaces.

From *man ifup*:> The  ifup  and  ifdown  commands  may be used to configure (or, respectively, deconfigure) network interfaces based on interface  definitions in the file /etc/network/interfaces.

---

