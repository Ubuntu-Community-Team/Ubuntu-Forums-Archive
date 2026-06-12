---
title: "82541PI Gigabit Ethernet Controller operates at 10 Mb/s"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by eombah on 2008-12-06
Hi,

I have a Dell Dimension 8300 with a gigabit nic.
NetworkManager tells me it is operating at 10 Mb/s, which I can confirm.

I have had it operating at 1Gb/s before, but somewhere along the Hardy upgrades this has changed.

I did a fresh install of Intrepid and the problem persists.

lspci tells me:

```
02:01.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev 05)
```

sudo ethtool eth0 tells me:

```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 10Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes
```

Any help is appreciated.

-Bart

---

### Post by jmoorse on 2008-12-07
Bart,

Try to manually set it to GigE (autonegotiation is not always so...automatic)

sudo ethtool -s eth0 speed 1000 autoneg off

If that drops your connection reset back to auto:

sudo ethtool -s eth0 autoneg on

Check the configuration of your switchport if this happens

---

### Post by eombah on 2008-12-07
Jeff,

Thanks for your answer.

   sudo ethtool -s eth0 speed 1000 autoneg off

dropped my connection. So I set it back to auto as you said:

   sudo ethtool -s eth0 autoneg on

and my connection came back after a few seconds, at 10 Mb/s.

You say:
> Check the configuration of your switchport if this happens 

What do you mean with that?

-Bart

---

### Post by jmoorse on 2008-12-07
Bart,

Is your ethernet cable plugged into a 1000Mbit capable switch?

Please respond with the make/model of the equipment on the other end of the ethernet cable.

thanks

---

### Post by eombah on 2008-12-08
Yes, it's a Linksys SD2008 8-Port 10/100/1000 Gigabit Switch.

Thanks,
-Bart

---

### Post by jmoorse on 2008-12-08
Please verify your cable is either Cat5e or Cat6

Please try a different switchport on the SD2008

---

### Post by eombah on 2008-12-13
My cable is Cat5. Another machine connected to the same switch with Cat5 cable connects at 100 Mbps, so my Dell Dimension 8300 with gigabit nic should be able to do that as well, as a minimum.
I know it has before.

Changing to a different port on the switch did not help.

-Bart

---

### Post by thornomad on 2008-12-17
Hello - wanted to jump in here and say I think I have the same problem (since a Hardy upgrade) -- only in my case, the NIC is stuck at 100MB/s (not 10).

Like the OP, it is connected to a gigabit router and it was functioning at full gigabit speeds prior to my upgrade to hardy (from dapper).  Also, using ethtool to force the speed to 1000 with autoneg off also drops my connection.  I have tried different CAT6 cables on different ports ... again, this happened after the upgrade.

Here are my details (lspci -nn):

```
00:0e.0 Ethernet controller [0200]: Intel Corporation 82541PI Gigabit Ethernet Controller [8086:107c] (rev 05)
```

Here is output from ethrool:

```
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: umbg
	Wake-on: g
	Current message level: 0x00000007 (7)
	Link detected: yes
```

Would be interested in any insight folks could provide.

Thanks,
Damon

---

### Post by midtown on 2008-12-17
Okay, this bug has been posted at [https://bugs.launchpad.net/bugs/309211](https://bugs.launchpad.net/bugs/309211), please subscribe to the report if it affects you and also click the "this bug affects me too" link, thanks!

---

