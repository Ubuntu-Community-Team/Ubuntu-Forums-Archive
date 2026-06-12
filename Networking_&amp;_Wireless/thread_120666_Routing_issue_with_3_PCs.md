---
title: "Routing issue with 3 PCs"
date: 2006-01-23
forum: Networking &amp; Wireless
---

### Post by mr_ed on 2006-01-23
We have been trying to run NistNet ([http://snad.ncsl.nist.gov/itg/nistnet/](http://snad.ncsl.nist.gov/itg/nistnet/)) at work, but we can't even get 2 PCs to talk to one another.

PC A is a laptop running Windows XP, IP address 192.168.1.100, netmask 255.255.255.0 and gateway set to 192.168.1.2

PC B is a server running Ubuntu Breezy, with eth0 at IP address 192.168.1.2, and eth1 at 192.168.2.1

PC C is a laptop running Ubuntu Breezy, IP address 192.168.2.101, netmask 255.255.255.0 and gateway set to 192.168.2.1

No matter how we've set up routes, we can't get A to talk to C and vice versa.

A can ping B eth0 AND eth1
C can ping B eth0 AND eth1
but A can't ping C.

Any ideas?

---

### Post by afhp on 2006-01-23
Is IP forwarding enabled on B ? (/etc/network/options)

---

### Post by mr_ed on 2006-01-23
YES, I changed /etc/network/options to allow IP forwarding.  I changed that, and then made the previous post, but I didn't reboot after setting it.  I tore down the the Ethernet interfaces to no avail...

After a reboot, everything seems to be working now.  Thanks!

There's now a sign on the computer that says "Touch it and die."  :)

---

### Post by mips on 2006-01-23
A bit late but anyway, [http://ubuntuforums.org/showthread.php?t=119787](http://ubuntuforums.org/showthread.php?t=119787)

Others could find it usefull.

---

