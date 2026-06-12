---
title: "Network Monitoring"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by zander x on 2013-06-13
Hello guys!

I've been tasked with a large project. I'm at a company with many Windows machines spread out across 5 islands. The project is to develop a network monitoring station that monitors the bandwidth and up/down status of the various internet connections. 

I guess it's like what NSA is doing, except we want to be able to look at the monitor and say "hey, the connection on XXX is slow/about to drop out" and know who/which machine is using the most bandwidth (along with very verbose statistics if possible). We're just keeping the connection up and fast, not storing the data being transmitted.

I've got EtherApe which doesn't quite do what I'm looking for. I can't get MRTG to work (UTF-8 error of some type), nload and pktstat. Pktstat is close and nload seems to give good data. I'm using a Dell Core Duo machine with U12.04.

I'll get two gold stars if I manage to find a way to make the same monitor monitor hard disk usage across a bunch of servers. I get a third star if all this is in a graphical format.

Hopefully someone out there can point me in the right direction.

---

### Post by Cheesemill on 2013-06-13
Take a look at Nagios and Cacti.

---

