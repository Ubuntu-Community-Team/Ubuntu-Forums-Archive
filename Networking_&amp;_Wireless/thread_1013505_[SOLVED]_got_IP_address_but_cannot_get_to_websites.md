---
title: "[SOLVED] got IP address but cannot get to websites"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by ieee488 on 2008-12-16
Ubuntu 8.04

I'm using AirCard 860 and using wvdialconf in Terminal window.

I can see that I am getting a local and a remote IP address
and a DNS address.

But I can't get to any websites in Firefox.

What am I missing?

---

### Post by ramaswamyps on 2008-12-16
type route in a konsole /terminal
should show similar to this
root@laptop:~# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
root@laptop:~#                          

you may need to sudo route


if you get a route check if firefox is offline.
check with any other browser
wget kget or something to download.

---

### Post by ieee488 on 2008-12-17
Boy, oh, boy.

I had not put Firefox in offline mode, but it was! :eek:

But that was it.

Thank you!

---

