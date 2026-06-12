---
title: "A few simple LAN questions"
date: 2011-06-19
forum: Networking &amp; Wireless
---

### Post by aeronutt on 2011-06-19
Trying to learn a bit about LANs, routers, etc.  I have two questions:


1) Using 'network tools' I ran a port scan to network address 192.168.1.1 (my wireless router), and got the following:

80 open www
1780 open unknown
10080 open amanda

What are the 1780 'unknown' and 10080 'amada' ports?

2) Can I use the network tool or iperf to measure the bandwidth between my laptop and my wireless router?

---

### Post by rickbeton on 2011-06-19
1) Amanda is open source backup/archive software
  [http://wiki.zmanda.com/index.php/Main_Page](http://wiki.zmanda.com/index.php/Main_Page)
More info on TCP ports (not including Amanda) here
  [http://en.wikipedia.org/wiki/Tcp_port_numbers](http://en.wikipedia.org/wiki/Tcp_port_numbers)

2) You'll need to time the transfer of files between the two for it to be meaningful. This is probably difficult because most routers don't have filestores and their web resources are typically not very big (leading to inaccurate measurements).  If you're lucky enough to have a router with a USB socket, you might be able to put a large file (video clip for example) and measure its access speed.

Rick

---

### Post by aeronutt on 2011-06-19
> **rickbeton said:**
> 1) Amanda is open source backup/archive software
  [http://wiki.zmanda.com/index.php/Main_Page](http://wiki.zmanda.com/index.php/Main_Page)
More info on TCP ports (not including Amanda) here
  [http://en.wikipedia.org/wiki/Tcp_port_numbers](http://en.wikipedia.org/wiki/Tcp_port_numbers)

2) You'll need to time the transfer of files between the two for it to be meaningful. This is probably difficult because most routers don't have filestores and their web resources are typically not very big (leading to inaccurate measurements).  If you're lucky enough to have a router with a USB socket, you might be able to put a large file (video clip for example) and measure its access speed.

Rick

1) Oddly, I'm not using Amanda, and don't even have it installed. Thanks for the links.
2) That make sense! Thanks. I don't have a USB port on my router. I'm just trying to learn, I haven't had any b/w problems.

---

