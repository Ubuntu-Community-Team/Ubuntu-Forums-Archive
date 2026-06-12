---
title: "Can't Ping localhost"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by lossanarch on 2013-03-07
Hi,

I've recently upgraded my vps ubuntu server from maverick to natty and now to oneiric and I've been trying all day to get Apache redirecting through a localhost proxy again (required for Dynmap - a minecraft map plugin - to work).

Finally I seem to have traced the problem back to the fact that localhost is pointing at 127.0.0.1 (and resolves to that when pinged) but ifconfig displays:
```
venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:5349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5146 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1027866 (1.0 MB)  TX bytes:3439874 (3.4 MB)


venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:96.8.122.219  P-t-P:96.8.122.219  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
```

If I'm reading that correctly there appears to be no 127.0.0.1 address, only a .2; I believe this is why apache redirection and pinging is failing.

How do I change .2 back to .1?

Thanks

---

### Post by lossanarch on 2013-03-11
Bump. Anyone have any ideas on this?

---

