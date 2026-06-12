---
title: "SiS190 Issue. Internet connectivity, but really slow."
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by MikeEnIke on 2010-03-05
Hey, I have karmic recently installed and working fine with pretty much everything. Only issue is with my sis190 drivers, my internet absolutely crawls. Downloads don't top 40kb/s and I'm on a university network that I've experienced downloading 1mb/s. I can ping, load most websites (albeit very slowly and maybe after a couple of refreshes) but it just doesn't work quite right. It's not even worth browsing the internet one. This is all eth0 by the way, wireless works just fine.

Are there any known solutions to a sis191 problem? I bumped my MTU down to 1250 cause I read that somewhere, and it's the only reason I can load web pages at all. 

Thanks for any help

---

### Post by chili555 on 2010-03-05
If you right-click the Network Manager icon and select Edit Connections and select your wired ethernet and click edit and then the IPv6 tab, does it read: Ignore?

---

### Post by MikeEnIke on 2010-03-05
> **chili555 said:**
> If you right-click the Network Manager icon and select Edit Connections and select your wired ethernet and click edit and then the IPv6 tab, does it read: Ignore?
Yup, sure does.

---

### Post by chili555 on 2010-03-05
How about, in a terminal, let us see:```
sudo ethtool eth0
```Thanks.

---

### Post by MikeEnIke on 2010-03-05
> mike@mike-laptop ~ $ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000037 (55)
	Link detected: yes


Thanks a lot for helping.

---

### Post by chili555 on 2010-03-05
> Speed: 10Mb/s
Duplex: HalfI wonder if things improve if you do:```
sudo ethtool eth0 -s speed 100 duplex full
```Your router or switch may or may not support it. If it works, we can amend a file somewhere to make it permanent.

---

### Post by MikeEnIke on 2010-03-05
> mike@mike-laptop ~ $ sudo ethtool eth0 -s speed 100 duplex full
ethtool: bad command line argument(s)
For more information run ethtool -h


Messed up argument in there somewhere? took out the -s and it put out the same error.

---

### Post by chili555 on 2010-03-05
Oops! Sorry. I must clean my trifocals some day soon...```
sudo ethtool -s eth0 speed 100 duplex full
```

---

### Post by MikeEnIke on 2010-03-05
> **chili555 said:**
> Oops! Sorry. I must clean my trifocals some day soon...```
sudo ethtool -s eth0 speed 100 duplex full
```

```
mike@mike-laptop ~ $ sudo ethtool -s eth0 speed 100 duplex full
mike@mike-laptop ~ $ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000037 (55)
	Link detected: yes

```

Hmm, didn't seem to effect it at all =/

---

### Post by chili555 on 2010-03-05
What does:```
sudo lshw -C network
```say that the driver is? After you find that, please do:```
dmesg | grep <driver>
```For example:> logical name: [COLOR="Blue"]eth0[/COLOR]
       version: 03
       serial: 99:0d:60:39:f5:88
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="Blue"]driver=e1000[/COLOR]```
dmesg | grep [COLOR="Blue"]e1000[/COLOR]
```Substitute your details, of course. Maybe we can "help" it.

---

