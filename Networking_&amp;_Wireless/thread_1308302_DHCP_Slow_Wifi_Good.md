---
title: "DHCP Slow Wifi Good"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by tosh0_11 on 2009-10-31
Hi,
 
My DHCP connection speed is 0.83Mb/s ... wireless connection on same router is 3.85Mb/s ... I am new to Linux and using Ubuntu 9.04. I have disabled ipv6 as suggested in other posts - but no change. 
 
NB. Win XP also on DHCP and connecting at high speeds
 
Any suggestions on how to improve speed?
 
Thanks

---

### Post by Yellobes on 2009-11-03
bump

msi card, netgear router, att service (256/56 kbps). Everything was all fine and dandy in 9.04, update to Karmic fixed that.

Pingtests rate 20 or so ms. even though it takes a full 15 seconds to ping.
Pageloads take ages not because of slow network but latency issues.
Been working on this for ages, google is appallingly unhelpful.

---

### Post by Yellobes on 2009-11-03
[https://bugs.launchpad.net/ubuntu/+bug/433972](https://bugs.launchpad.net/ubuntu/+bug/433972)

something.

---

### Post by Yellobes on 2009-11-03
in my case, it was a dns problem.

go to [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/) and get some dns for your soul
find your router's IP

network settings > edit connections > network adapter (find the one in use and hit edit)

IPv4 tab > DHCP (addresses only)
>DNS servers- take those ones from dnsserverlist.org and paste two of em, separated by commas, followed by your router IP

IPv6 tab > ignore

now disable networking and re-enable it to restart it

thumbs up or thumbs down?

---

### Post by Yellobes on 2010-09-30
Google DNS (8.8.8.8  and 8.8.4.4)

---

