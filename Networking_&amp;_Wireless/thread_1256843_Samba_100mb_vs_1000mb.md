---
title: "Samba 100mb vs 1000mb?"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2009-09-03
Ok so when i transfered a file from windows to ubuntu i noticed i was only getting about 9.3mb/s avg. so then i checked ethtool and speed was advertised at 100mbs which means avg download speed will hit around 12ish from waht i understand and my experience.

so then i typed this in to terminal
```
sudo ethtool -s eth0 speed 1000 duplex full
```

and then trasnsfer the same file and got only 7.6mbs
why is that is there some other settings i should change... thanks

ok just realized that the settings dont really take affect

Here is the ethtool results when i type
```
sudo ethtool -s eth0 speed 100 duplex full
```
```
Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 7
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

```

and it is the same after this
```
sudo ethtool -s eth0 speed 1000 duplex full
```

---

### Post by ductiletoaster on 2009-09-03
Hate to reply to my own thread but i totally forgot the two computers are plugged into a linksys router (which i turned into a wireless bridge) and its a 100mb switch.

---

