---
title: "dhclient takes a very long time"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by atisho on 2013-01-10
I set up a macvlan and assign it IP address thru DHCP by using dhclient.  This has worked fine until this morning.  The following is what happens now:

$ sudo ip link add dev veth0 link eth0 type macvlan
$ sudo dhclient veth0
(....took so long to finish here.  Then the following message appears: )
PING 10.10.0.1 (10.10.0.1) 56(84) bytes of data.

--- 10.10.0.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.511/0.511/0.511/0.000 ms
$

dhclient still works but now it just takes so much longer(a few minutes at least).  Anyone can shed me some light?

I am running Ubuntu 12.04 64bit.

Thanks in advance

---

