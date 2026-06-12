---
title: "Shorewall, ipset v2.5.0 and kernel 2.6.31-20-generic"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by DrJohn999 on 2010-03-18
(Karmic, Samsung NC10, runs great, no complaints)

This laptop has two interfaces: eth0 and wlan0, then I've added a pptp vpn to work, and an OpenVPN connection to the server @ home. Shorewall does a great job of managing all this, and plays well with the Shorewall setup on the home server. However, the behavior I want when connected thru eth0 or wlan0 at home is not the same as when out and about. At home I want these interfaces to be local zones and accept appropriate traffic, while on the road they should behave as net interfaces and accept only much more restricted traffic. The IP address of the interface isn't a good way to do this, although I could use a very unique set of IPs at home. Mac addresses seem better.

The ipset capability in Shorewall plus appropriate host and zone files should provide this capability via macipmap ipsets, but ipset functionality seems to be broken for ipset v2.5.0 and kernel 2.6.31-20-generic:

```
/etc/shorewall$ sudo ipset --list
FATAL: Module ip_set not found.
ipset v2.5.0: Error from kernel: Protocol not available

```
I'm not into rebuilding the kernel -- any solutions out there to get this running?

---

### Post by DreamDemon on 2010-10-31
I have the same issue.  In 10.04 i was able to use module-assistant to create the modules without recompiling the kernel but it is failing this round with that exact same message.  As a bonus, version 4.4 of ipset is available currently.

---

### Post by pepoluan on 2011-01-22
Here's what I did:
[LIST=1]
[*]Remove ipset using aptitude
[*]Install gcc using aptitude
[*]Download the latest ipset from [it's site]("http://ipset.netfilter.org/install.html")
[*]Extract the ipset source
[*]**make **then **make install** then **make clean**
[*]**depmod -A**
[*]**modprobe ip_set**
[/LIST]

No need to rebuild kernel, methinks.

---

