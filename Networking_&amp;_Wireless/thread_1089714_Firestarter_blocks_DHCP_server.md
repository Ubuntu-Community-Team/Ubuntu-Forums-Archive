---
title: "Firestarter blocks DHCP server"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by The Foz on 2009-03-07
I am having a problem getting my DHCP server to work with the Firestarter firewall.

I am using dnsmasq as my DHCP server. It works fine (both a DNS forwarder and as a DHCP server), as long as Firestarter is off (i.e. not started at all, or "stopped"). As soon as I start the firewall, DHCP stops working.

I have tried lots of different configuration options in Firestarter, but no joy.

I have read the online documentation for Firestarter. It seems that it is designed to work only with certain DHCP servers; for Debian based systems, this is "dhcp", which is now obsolete!

I tried installing the current Ubuntu recommended DHCP server, dhcp3-server (after disabling the DHCP functionality in dnsmasq - and yes, I did test that it was disabled), but still no DHCP once Firestarter was started (plus I got an error from Firestarter).

The Firestarter documentation says that Firestarter will "manage" the DHCP server daemon for you (if it can find it). Clearly it can't find either dnsmasq or dhcp3-server. What seems to be happening is that, when it fails to find a recognised DHCP server, it somehow blocks the DHCP traffic.

Does anyone know a way to force Firestarter to allow the DHCP traffic?

I don't want to change to another firewall solution, as I like Firestarter, and I use it's Internet Connection Sharing for the other machines on the network.

---

### Post by The Foz on 2009-03-11
Bump!

---

### Post by muximus on 2009-05-05
Known bug, bugfix at the following link:
[https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/43784](https://bugs.launchpad.net/ubuntu/+source/firestarter/+bug/43784)

---

