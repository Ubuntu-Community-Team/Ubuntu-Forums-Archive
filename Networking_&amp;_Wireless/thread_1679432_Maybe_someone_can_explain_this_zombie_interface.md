---
title: "Maybe someone can explain this zombie interface"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by mrpaco on 2011-02-01
I have a server running 10.04 with two identical NICs.  Each has a static IP directly connected to the internet (and these IPs are next to each other, eg eth0 is 192.168.1.101 and eth1 is 192.168.1.102).  Funny thing about this config is that when a cable is connected to both simultaneously, only eth1 is accessible, yet when a cable is removed from either port, BOTH magically become accessible, which is REALLY ******* WEIRD.  The only thing I can think of is that I implemented a bridged connection to eth0 for KVM, but for a variety of reasons never installed any VMs.  Perhaps the bridge has taken over the IP assigned to eth1, so everything crashes and burns when a physical connection is present.  I would LOVE to hear your thoughts on the matter.

---

### Post by mips on 2011-02-01
You cannot have two interfaces in the same network without causing problems.

[http://ubuntuforums.org/showpost.php?p=668900&postcount=11](http://ubuntuforums.org/showpost.php?p=668900&postcount=11)



.

---

