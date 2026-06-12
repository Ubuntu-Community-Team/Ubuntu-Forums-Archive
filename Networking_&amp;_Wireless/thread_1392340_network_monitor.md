---
title: "network monitor"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by 7SEALS on 2010-01-28
I wish to setup my spare PC as a router

I was wondering what programs, in ubuntu, I can use to monitor and change settings concerning bandwidth useage

I want to throttle down a computer in my network so what program would be good for this? Thanks in advance.

---

### Post by johnson.d on 2010-02-02
1)For monitoring the bandwidth 'nagios' ([http://www.nagios.org/](http://www.nagios.org/)) can be used. It can be installed by using the command 'apt-get install nagios3'
2)For controlling the bandwidth 'tc' command can be used. This is bundled in iproute2 in Ubuntu and installed by default.

The details for routing and bandwidth control can be found at [http://lartc.org/howto/](http://lartc.org/howto/)

---

