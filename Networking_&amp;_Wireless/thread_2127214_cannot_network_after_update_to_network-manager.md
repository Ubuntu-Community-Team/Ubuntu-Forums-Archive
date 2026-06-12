---
title: "cannot network after update to network-manager"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by oscarkramer on 2013-03-19
After an automatic update on 3/15 that included network-manager 0.9.4.0-0ubuntu4.2, I restarted and I got a boot message: "waiting up to 60 seconds for network connection." I was able to re-establish connectivity by adding explicit network config data into /etc/network/interfaces, namely:

```

auto eth0
iface eth0 inet static
           address 192.168.0.171
           netmask 255.255.255.0
           broadcast 192.168.0.255
           gateway 192.168.0.1

```

Before the update (running network-manager 0.9.4.0-0ubuntu3), I did not have any entry for eth0 but it still worked. I reverted to version ubuntu3 and removed my edits to /etc/network/interfaces (effectively reverted everything) and all works fine. 

Does anybody know what is happening with the latest network-manager update? I don't want to leave explicit IP info in /etc/network/interfaces as I frequently connect to other networks and need auto config to work.

---

