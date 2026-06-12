---
title: "Routing - Can't add routes"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by terminus1 on 2011-09-30
Hi,

I have a laptop with Ubuntu 9.04 and two NICs (built-in and a PCcard) and I'm attempting to setup routing, following the guide at [http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/]("http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/").

In Network Manager, I have:
eth0 10.10.10.21 (in-built NIC), with one route:
[INDENT]10.10.10.2   255.255.255.255   10.10.10.21   1[/INDENT]
eth1 10.10.10.20 (PCcard NIC), with one route:
[INDENT]10.10.10.1   255.255.255.255   10.10.10.20   1[/INDENT]

I've added the admin table to /etc/iproute2/rt_tables:
#
# reserved values
#
255	local
254	main
253	default
0	unspec
#
# local
#
#1	inr.ruhep
1 admin

My next step is to add two routes, as seen from the command line:
root@ubuntu:/etc/iproute2# ip route add 10.10.10.1 dev eth1 src 10.10.10.20 table admin
root@ubuntu:/etc/iproute2# ip route add 10.10.10.2 dev eth0 src 10.10.10.21 table admin

Looking at the result, I cannot find the new routes. Why not?
root@ubuntu:/etc/iproute2# ip route show
10.10.10.0/24 dev eth0  proto kernel  scope link  src 10.10.10.21  metric 1 
10.10.10.0/24 dev eth1  proto kernel  scope link  src 10.10.10.20  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 
default via 10.10.10.20 dev eth0  proto static

The routes that exist above are from the Network Manager entries I created. 

What am I (routing noobie) doing wrong?
Thanks!

---

### Post by terminus1 on 2011-09-30
I was wrong about the routes shown being due to the routes in the Network Manager; I deleted them and IP Route Show results are the same.

If I use a different syntax for the Prefix, I get RTNETLINK answers: invalid argument.
ip route add 10.10.10.1/24 dev eth1 src 10.10.10.20 table admin

Adding the "/24" is illegal? Doesn't make sense.

---

### Post by terminus1 on 2011-09-30
ah! (facepalm) I get it.
use 10.10.10.1/32, not 10.10.10.1/24

---

