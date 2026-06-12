---
title: "Internet connection sharing -again!!"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by malcmail on 2011-11-04
I've had this working before but after a rebuild and the like I've hit a bit of a roadblock. My ubuntu box is wireless to my router. This is then supposed to share a connection with a FreeNAS box via ethernet cable. 

The ubuntu box has the eth0 port set to be shared and I've removed all the iptables rules as this caused me a total headache before. I've assigned a static IP to the FreeNAS box within the same subnet as the eth0 port on the ubuntu box. But I can't get them to ping each other at all.

Anyone got any ideas where I've gone wrong here?

TIA

---

### Post by malcmail on 2011-11-04
The BSD box seems to be trying to use a fwe0 interface which I've heard is firewire - odd as its usually rl0 being the railink on the mobo (I think)

---

### Post by malcmail on 2011-11-04
Solved using this - it was automtically finding the wrong interface.

[http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=38&t=7325&start=0](http://sourceforge.net/apps/phpbb/freenas/viewtopic.php?f=38&t=7325&start=0)

---

