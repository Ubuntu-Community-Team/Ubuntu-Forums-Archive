---
title: "changing dhclient3 flags"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by pliit on 2011-09-02
Hey.


I'm using 11.04. Have removed network-manager and configuring my network devices from /etc/network/interfaces

So I'm using dhcp for one device and everything is working good, except I can't find where are the flags set for dhclient3.

Currently it's running as "dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp3/dhclient.eth0.le
ases eth0"

And I can't find where are those flags set.
I tried looking in /sbin/dhclient-script, but I don't think it's there.

Basically the problem is that my ISPs DHCP lease time is 300 and the DHCP client keeps spaming logs because of this. Would like to change that.

Any ideas?


Thank you.

---

### Post by gmargo on 2011-09-02
The **/sbin/dhclient3** daemon is spawned by the **/sbin/ifup** command.  See the source for the **ifupdown** package for the gory details.

---

