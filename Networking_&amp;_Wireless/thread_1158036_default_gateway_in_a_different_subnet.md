---
title: "default gateway in a different subnet"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by gastur on 2009-05-13
Hello all!

Sometimes there is need to set up default route through a gateway which is on a subnet different from the one assigned to host's network interface. The problem is (just for example):

eth0 192.168.**1**.10/24
gw1 192.168.1.1/24 (knows route to 192.168.2.x)
gefault gw 192.168.**2**.1/24

Used command sequence:

1. route delete default
2. route add -net 192.168.2.0 netmask 255.255.255.0 gw 192.168.1.1
(or route add -host 192.168.2.1 gw 192.168.1.1)
3. route add default gw 192.168.2.1 (or route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.2.1)

Command #3 fails with warning:
SIOCADDRT: No such process
though assumed default gw (192.168.2.1) is pinged OK and route to it is in the routing table.

Update:
**Solved**. Abovementioned behaviour is reasonable and standards compliant, so no real problem here. Sorry for dumb question.

---

### Post by braingram on 2009-07-01
I'm a bit confused here. So having a default gateway on a different subnet (so static ip = 192.168.1.10 gateway = 192.168.2.1) is impossible because it's not 'standards compliant'?

I ask because this would mean the network I am trying to connect to is not standards compliant. If so, I will be unable to connect to it using linux?

Is there no way to set a default gateway with a different subnet?

---

