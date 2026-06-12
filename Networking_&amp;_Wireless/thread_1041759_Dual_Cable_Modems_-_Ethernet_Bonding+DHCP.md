---
title: "Dual Cable Modems - Ethernet Bonding+DHCP"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by ChriSterling on 2009-01-16
Hello all, 
Requesting assistance with dual wan cable modem sharing.

Setup:
2 cable modems
1 Ubuntu 8.10 box with 3 nics

Goal:
use both modems to eth0 and eth1 simultaneously with arp trickery eth-bonding driver in mode6 or balance-alb,

and use 3rd nic (eth2) to act as dhcp server to my wireless access point that will feed the home.

( or, if needed to simplify, just staticly feed to my wireless router and let the router handle dhcp.)

# i'm desperate to solve this
Thank You!!
Chris

---

### Post by ChriSterling on 2009-01-18
I've tried all tutorials and guide that seem to touch on this topic to no avail.

Is there a mock scenario or tutorial that exists with someone combining two modems into one with any flavour or unix derivative.  Likely reffered to as link aggregation, ethernet bonding, teaming nics, or load balancing.

---

### Post by ChriSterling on 2009-01-18
Now i'm basically begging and groveling for help humbly with no sense of pride left. 

Cashing out any equity i've built up in my pride for some assistance here!

bump

---

### Post by jbarbieri on 2010-01-18
[http://ubuntuforums.org/showthread.php?p=8129464](http://ubuntuforums.org/showthread.php?p=8129464)

Should work for you.

---

