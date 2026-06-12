---
title: "Lost virtual interfaces support /etc/network/interfaces 9.10 Karmic"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by PorcelainMouse on 2009-11-23
Does anyone know how to get virtual interfaces working?  I've been using a virtual interface in /etc/network/interfaces since Gutsy Gibbon and now 9.10 Karmic it doesn't work at all.  This used to work just fine:

#auto eth2:1
#iface eth2:1 inet static
#  address <ip>
#  network <subnet>
#  netmask 255.255.255.0
#  gateway <gw>

Now it fails miserably.  ifup thinks its a duplicate, presumably of eth2:0 or eth0.  There was a post describing this exact menthod two months ago on an on-line Linux magazine, so I don't understand what happened.  And there's no mention of this behavior change in the ifupdown package.

---

