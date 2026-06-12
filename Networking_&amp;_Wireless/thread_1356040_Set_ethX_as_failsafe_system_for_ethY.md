---
title: "Set ethX as failsafe system for ethY"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by vexy on 2009-12-15
How could I set/configure eth2 to be a failsafe system for eth1, in case eth1 fails for some time. eth2 should be temporary static configured. When eth1 goes up, close eth2. eth1 must be static configured and starts up with the system boot-up.

Thank you.

---

### Post by t0mppa on 2009-12-15
Well, you could configure them both available and enable load balancing. That way if one goes down, the other is naturally used. Or alternatively make a script for taking eth1 down that loads eth2 up, if you're only worried about downtime caused by the user.

Either of these sound any good for your situation? Not sure, if you can pick up a possible networking failure on eth1 easily and act on it automatically by firing up another connection.

---

### Post by vexy on 2009-12-16
Very well, but if eth1 fails, and eth2 (naturally) starts, how could I know (or the server) if eth1 came up. In this case eth2 should stop and eth1 continue eth2's activity. Does this naturally happens ? I am afraid it doesn't.

---

### Post by t0mppa on 2009-12-16
Well, I did some further digging and found this tutorial for [Dead Gateway Detection]("http://www.ssi.bg/~ja/dgd-usage.txt"), which sounds like just the thing you're looking for, it's just a little old as a document.

---

### Post by uniden9 on 2009-12-16
Why not setup Active-backup network bonding?
You just add the ethX and ethY as network interface slaves and configure your ip/gateways and service to run off the bonding sudo interface bond0. The bonding device drivers does the failing over/ fail back.  I would only recommend Active-backup and ether channel 802.3ad, because the round robin and xor types confuse your switches arp tables when you try to use both nic's as active sending interfaces.

For more on this, see:
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by t0mppa on 2009-12-17
Never knew bonding had that many useful applications, just thought it was good for sharing network connections forward. Always nice to learn something new though. And it looks like a perfect solution for the problem at hand too, does what OP wanted and simple to set up.

---

