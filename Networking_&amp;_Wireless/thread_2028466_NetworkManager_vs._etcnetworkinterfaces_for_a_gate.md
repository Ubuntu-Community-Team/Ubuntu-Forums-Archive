---
title: "NetworkManager vs. /etc/network/interfaces for a gateway machine"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by ahardy66 on 2012-07-18
I've got a new installation of 12.04 on my gateway machine for my soho lan. 

I'm moving across from an older machine where I'd run debian for ages and I figured I prefer the UI with Ubuntu so here I am. 

I'm in the process of setting up my two network cards, one to the DSL modem and one to the lan wireless access point, along with dnsmasq and iptables. 

Now I've discovered that Ubuntu has Upstart for booting, and NetworkManager and all its functionality. I'm wondering whether to go with NetworkManager, or to remove it and stick with /etc/network/interfaces way of doing things.

Anyone got any recommendations? My initial impression is that NetworkManager is not meant for this - it's aimed squarely at workstations, not servers.

---

### Post by Sergius14 on 2012-07-18
The Server edition lacks Network Manager and you configure everything by hand.

You may try the Server edition. 

It doesn't come with GUI by default but you can add it later through apt-get.

---

### Post by chili555 on 2012-07-18
> My initial impression is that NetworkManager is not meant for this - it's aimed squarely at workstations, not servers.Correct. Network Manager will struggle to do what you are trying to do, if it will at all. You already know how to do /etc/network/interfaces; I'd stick with it.

---

