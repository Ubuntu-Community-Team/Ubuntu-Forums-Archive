---
title: "Bring up network interface at start without configuring them"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by klockren on 2010-10-22
I use my Ubuntu Maverick box for virtualization and I bridge my VMware guests to eth1 and eth2. But I don't want my ubuntu box itself on the network...

On my Gentoo boxes, I just add
[INDENT]config_eth0=( "null" )
config_eth1=( "null" )[/INDENT]
to /etc/conf.d/net and eth0+1 will be upp but not configured with an IP.

So, how can I do this with Ubuntu? I believe that I could solve this by entering
[INDENT]# update-rc.d -f networking remove[/INDENT]
and then add
[INDENT]ifconfig eth0 up
ifconfig eth1 up[/INDENT]
to /etc/rc.local, but that does look like an ugly solution.

Cheers,
klockren

---

