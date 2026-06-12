---
title: "Disable Persistent Net Rules MAC address"
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by garyamort on 2011-11-30
I've been using Ubuntu in Oracle's VirtualBox for a dev environment.  One problem I've run into though is how it defaults to storing the MAC address of the network cards.  If I clone a system and give it new network interfaces, ubuntu has the old MAC addresses stored and won't bring up the new ones.

Is there a way to disable this feature?  I would think there is since I never have a problem when running on a virtual host in Amazon's EC2.

For reference purposes, here is a link about how to edit the rules file when changing physical network cards.
[http://davebour.com/linux/changing-network-card-in-ubuntu.html](http://davebour.com/linux/changing-network-card-in-ubuntu.html)

---

