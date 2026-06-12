---
title: "portable installs, network issues"
date: 2012-01-19
forum: Networking &amp; Wireless
---

### Post by i.r.id10t on 2012-01-19
So my students install Ubuntu (10.04) to an external drive to use as their environment for my class.  The udev rules indicate that when a new MAC address is found, to bump up the eth device number.  Student installs while at machine A, they have eth0.  Boot up at home, they have eth1, boot on machine B in the lab, they have eth3 and so on.  Causes issues w/ dhcp on boot, possibly due to network manager.

Whats the best way to solve this?  I'm thinking replace the MAC address in the /etc/udev/rules.d/70-persistent-net.rules file with an asterisk will do it.

Is there a better way? Or an "Ubuntu way"?

---

