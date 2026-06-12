---
title: "PPPoE stopped working"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by tackatucka on 2009-10-25
hi,

i set up my internet connection with pppoeconfig on hardy few days ago and it worked fine with dynamic ip.

Today it stopped working for no reason. I didnt change any settings!
I am using the same router with my backup-pc now. The router and isp seem to work fine.

I tried to run pppoeconf again and it doesnt find an access-concentrator while scanning my ethernet ports.

here are some outputs of my terminal i have no clue what the problem is :confused:

> 
plog output:
------------
pppd[5680]:Timeout waiting for PADO packets
pppd[5680]:Unable to complete PPPoE Discovery

ifconfig output:
----------------

eth0 Link encap:Ethernet Hardware Adress 00:16:d3:4c:ae85
inet6-adress: fe80::216:d3ff:fe4:ae85/64 scope: link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 MB)

dhclient eth0:
--------------
...
No DHCPOFFERS received


i have the feeling that my eth0 isnt working as it should but i have no clue if thats the problem or how to fix it.

help would be highly appreciated

---

### Post by tackatucka on 2009-10-25
still no clue why my PPPoE connection refused to work but i managed to get it up again.

just changed the etc/network/interfaces file. After rebooting pppoeconf could set up a new connection.

this is how my interfaces file looked like before using pppoeconf.
> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp

---

