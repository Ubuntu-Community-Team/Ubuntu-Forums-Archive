---
title: "Ubuntu 10.04 wired internet stops working constantly"
date: 2013-06-23
forum: Networking &amp; Wireless
---

### Post by gfixler on 2013-06-23
I can get it to start up again with this (before I learned this I was rebooting all the time):

```
$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 9248
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/48:5b:39:17:03:df
Sending on   LPF/eth0/48:5b:39:17:03:df
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 38343 seconds.

```

It always works for a little bit, then stops again.

I'm on 64-bit Ubuntu 10.04. I thought it might be unique to this machine, but it started happening recently at work on quite a different computer, which I *think* is 32-bit. It feels like an update to 10.04 a few months ago might be the culprit, but I have no idea. I've searched Google now and again for months with no luck.

---

