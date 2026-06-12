---
title: "Wake-On-Lan not working"
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by BioGeek on 2009-12-20
Hi, I have an old computer that I now want to use as an headless server. It has an ASUSTek CUV4X-E motherboard. I went into the BIOS settings to Power Up Control and enabled "PWR Up On External Modem Act" and "Wake On LAN or PCI Modem".

But when I check with 

```
$ sudo ethtool eth0
``` I get:
```

Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 24
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000001 (1)
	Link detected: yes

```

I would have expected a line like 
```
        Supports Wake-on: pg 
```
in that list.

And indeed, when I do 
```
$ sudo ethtool -s eth0 wol g
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol

```

So, how can I get Wake-On-Lan to work in ubuntu 9.10 on this machine? I suppose that, since I can enable it in the BIOS, it must somehow be possible.

Thanks in advance.

---

### Post by SteveDee on 2009-12-20
Yes it is possible, see here: [http://ubuntuforums.org/showthread.php?t=1340322](http://ubuntuforums.org/showthread.php?t=1340322)


Emergency edit: Uh-Oh! I didn't read your post properly. To Wake-On-LAN try to install wakeonlan via a terminal:-
sudo apt-get install wakeonlan

Now turn on with:-
ethtool -s eth3 wol g

Power down, but leave power connected.

Then issue a wake instruction remotely using the broadcast address for your network and the MAC address for the machine you want to wake. Example:-
wakeonlan -i 200.1.1.255 00:19:db:25:a7:03

If this works you need to put the ethtool command (above) in a script, because this needs to be reset each time your computer runs.

---

