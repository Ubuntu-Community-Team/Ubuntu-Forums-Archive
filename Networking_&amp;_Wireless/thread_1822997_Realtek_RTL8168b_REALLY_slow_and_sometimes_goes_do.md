---
title: "Realtek RTL8168b REALLY slow and sometimes goes down completley"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by lillem4n on 2011-08-11
Exactly the same computer have no network issues at all, when on windows.

It is a fresh install of Ubuntu 10.04 LTS 64 bit desktop. I have installed the proprietary driver for my nvidia card.

My motherboard is Asus P8P67 rev 3.0

Using scp, I'm getting 100-500kb/sec, if I get a connection at all. I have tried 2 different switches (both working fine in windows, though). Network goes down completley every 2 min or so, and is gone for 30 sec.

Some output:

dmesg | grep eth0:

[    1.265601] eth0: RTL8168b/8111b at 0xffffc90000676000, f4:6d:04:9c:7f:d6, XID 0c900800 IRQ 33
[    2.773959] r8169: eth0: link down
[    2.773974] r8169: eth0: link down
[    2.774222] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    6.095888] r8169: eth0: link up
[    6.096113] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.533256] eth0: no IPv6 routers present
[   61.890977] r8169: eth0: link up
[   62.230428] r8169: eth0: link up
[  143.904763] r8169: eth0: link up
[  182.972836] r8169: eth0: link up
(the "link up" continues a LOT. More and more are adding as the computer stays on)

======================

sudo ethtool eth0 says:
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

---

### Post by Kromgol on 2011-08-12
I have the same problem with RTL8168b, and you can see my thread here: [https://bbs.archlinux.org/viewtopic.php?pid=974836](https://bbs.archlinux.org/viewtopic.php?pid=974836)

Hopefully it's going to be solved.

---

### Post by varunendra on 2011-08-12
Hmm.. looks like you have the same problem (r8169 driver for r8168b chip) and therefore the same solution as this one:
[http://ubuntuforums.org/showpost.php?p=11053381&postcount=6](http://ubuntuforums.org/showpost.php?p=11053381&postcount=6)


Hope it works for you as it has for a couple of other guys :)



**_EDIT_:**
I have included some additional info in the above linked post under 'Edits' that may address problems with kernel 3 also as mentioned in post #6 below.

---

### Post by Kromgol on 2011-08-13
Wow, it was really that simple? And i ended up buying a new network card. Oh well.

---

### Post by varunendra on 2011-08-13
> **Kromgol said:**
> Wow, it was really that simple? And i ended up buying a new network card. Oh well.
At least you have an extra one now! :popcorn:
Plus, now you can help out others having same card..;)

---

### Post by Kromgol on 2011-08-13
> **varunendra said:**
> At least you have an extra one now! :popcorn:
Plus, now you can help out others having same card..;)

lol

Yeah well, i still tried your fix out and i didn't get it to work as apparently the module did not get created and therefore couldn't get probed, most probably because it's only supported with 2.6.x and i'm running 3.x on Arch.

Hopefully Realtek will release an updated version of it, or i will have to mail them and ask. I also hope this will get fixed in a later version of the kernel, should probably write a bug report of it as the kernel should have support for it since around 2.4 i think.

---

