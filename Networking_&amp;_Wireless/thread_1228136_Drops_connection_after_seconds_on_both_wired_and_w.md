---
title: "Drops connection after seconds on both wired and wireless"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by qianian on 2009-07-31
How can I stay online for more than a few seconds at a time? Wired connection was fine at home yesterday, then I connected to wireless at a cafe I frequent regularly, when it started disconnecting after less than a minute. Same thing back on wired connection.

I'm using dhclient to re-connect. For months now I've had to use it to connect to wired on reboot.

Here's the output:

There is already a pid file /var/run/dhclient.pid with pid 10084
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth1/00:1b:77:b0:cd:f8
Sending on   LPF/eth1/00:1b:77:b0:cd:f8
Listening on LPF/eth0/00:15:58:c8:c6:03
Sending on   LPF/eth0/00:15:58:c8:c6:03
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST of 192.168.1.152 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.107 on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 4
DHCPACK of 192.168.1.107 from 192.168.1.1
bound to 192.168.1.107 -- renewal in 36417 seconds.

I'm running Ubuntu 8.04 on lenovo ThinkPad R61i. 

Thanks.

---

### Post by Crafty Kisses on 2009-08-03
When the connection drops, are you able to ping websites and receive replies? Try:
```
ping google.com
```

---

### Post by qianian on 2009-08-10
The problem spontaneously went away. I haven't been able to duplicate it.

No, it would hang on ping.

---

