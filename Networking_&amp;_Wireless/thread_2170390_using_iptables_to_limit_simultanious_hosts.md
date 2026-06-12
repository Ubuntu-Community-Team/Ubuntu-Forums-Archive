---
title: "using iptables to limit simultanious hosts"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by flameheap on 2013-08-26
Hi!
I have the following situation: there is a server that can be acccessed from several different class C networks. I need to allow not more than 10 different hosts from each subnet to access this server simultaniously. Every host can open unlimited number of connections, so standard hashlimit cannot be used.
For example: there is a sever with address 192.168.230.40, that can be accessed by hosts from subnet 192.168.65.0/24 and from subnet 192.168.43.0/24. I need an iptable rule(s) that drops packet from any new client IP if there are established connections by 10 different IPs of the same subnet already.
Can anyone suggest something to solve this?
Thanks!

---

### Post by SeijiSensei on 2013-08-26
I don't know if you can do this with iptables, but you might look into "wrapping" the services offered using xinetd.  Xinetd listens on all ports and spawns connections to services for which it has a corresponding configuration file.  The "instances" option in xinetd lets you limit the number of connections, though I don't know whether you can have the rule apply separately to different subnets.  Read the [xinetd.conf](http://linux.die.net/man/5/xinetd.conf) man page for details.

---

