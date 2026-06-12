---
title: "speed up eth0 (from 10 Mb/s to 100 Mb/s)"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by Helios89 on 2009-05-19
Hi folks,

today i checked if WOL (wake on lan) was enabled in my network card, and i noticed this thing:

```
davide@hati:~$ sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	**Speed: 10Mb/s**
	Duplex: Half
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: no

```

That 10 Mb/s worried me a bit. I checked on my router/switch/modem and there is another pc with 100 Mb/s Full Duplex.

How can I set my eth card to 100 Mb/s? Will this change improve the speed of file transfer between pc on that LAN?

```
sudo ethtool -s eth0 speed 1000
``` isn't useful at all. (I can't change also duplex to full)

I'm sure I have a 10/100/1000 Card (but I don't remember how to see which one)

---

### Post by Nostalos on 2009-05-19
You can't set the speed of the interface with Auto Negotiation still on.

> 
sudo ethtool -s eth0 autoneg off
sudo ethtool -s eth0 speed 100 (or 1000 only if your switch supports it)
sudo ethtool -s eth0 duplex full


However do note that your switch will need to be set to the same speed/duplex settings.  If not it will try to continue autonegotation and your server wont.   You will end up with late collisions and data transfers far worse that 10mbit.

---

### Post by coubi64 on 2009-06-29
Thanks for your help.

Is it possible to keep it permanently (not having to do this at each startup)?

The solution to add these lines to /etc/network/interfaces is not a "clean" solution for me (only having 2 lines with lo interfaces in this file, to work correctly with network-manager)

---

### Post by iponeverything on 2009-06-29
> 
Is it possible to keep it permanently (not having to do this at each startup)?

yes, you could get a ethernet card that will auto-negotiate  correctly.

or you could just add the lines to /etc/rc.local to run at boot.

```

cat /etc/rc.local|grep -v ^exit  >> /tmp/rc.local
echo ethtool -s eth0 autoneg off >> /tmp/rc.local
echo ethtool -s eth0 speed 100   >> /tmp/rc.local
echo ethtool -s eth0 duplex full >> /tmp/rc.local
echo exit 0 >> /tmp/rc.local
sudo cp /etc/rc.local /etc/rc.local.orig
sudo cp /tmp/rc.local /etc/rc.local

```

---

### Post by coubi64 on 2009-07-04
Thanks a lot, it worked ;)

---

