---
title: "Disabling IPV6 Autoconfigure in Ubuntu 12.04"
date: 2013-04-06
forum: Networking &amp; Wireless
---

### Post by sandyd on 2013-04-06
For some reason, some of the servers in the datacenter that I am hosted in are sending out ipv6 autoconfiguration - I currently have around 6 global addresses that mysteriously appear whenever I start my server.

For some reason, adding
```
net.ipv6.conf.all.autoconf = 0
net.ipv6.conf.all.accept_ra = 0
```
in sysctl.conf (and rebooting) does nothing.

I can disable ipv6 with
```
net.ipv6.conf.all.disable_ipv6 = 1
```, but I do want to add my own personal ipv6 addresses in the future.

Any ideas?
I see the bug at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/997605](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/997605) , but the last poster says that it has been resolved.

---

