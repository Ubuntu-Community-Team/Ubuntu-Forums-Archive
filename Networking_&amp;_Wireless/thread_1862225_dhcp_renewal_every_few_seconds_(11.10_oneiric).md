---
title: "dhcp renewal every few seconds (11.10 oneiric)"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by Enucatl on 2011-10-16
Hi,
I installed Kubuntu 11.10 today, and I'm experiencing the following network issue: I'm getting a very short dhcp lease time, which doesn't happen if I boot Lucid Lynx on the same computer and network. I tried removing network-manager and installing wicd. I also disabled ipv6. That helped with the speed of the connection but no luck on these frequent disconnections.

Needless to say I can't do much on the internet: no downloads, no svn checkouts...


cat /var/sys/syslog

```
Oct 16 18:57:02 matteo dhclient: bound to 10.192.9.23 -- renewal in 293 seconds.
Oct 16 18:58:09 matteo kernel: [ 1602.812314] usb 1-5.4: reset high speed USB device number 5 using ehci_hcd
Oct 16 19:01:55 matteo dhclient: DHCPREQUEST of 10.192.9.23 on eth1 to 10.192.0.1 port 67
Oct 16 19:01:55 matteo dhclient: DHCPACK of 10.192.9.23 from 10.192.0.1
Oct 16 19:01:55 matteo dhclient: bound to 10.192.9.23 -- renewal in 252 seconds.
Oct 16 19:06:07 matteo dhclient: DHCPREQUEST of 10.192.9.23 on eth1 to 10.192.0.1 port 67
Oct 16 19:06:07 matteo dhclient: DHCPACK of 10.192.9.23 from 10.192.0.1
Oct 16 19:06:07 matteo dhclient: bound to 10.192.9.23 -- renewal in 291 seconds.
Oct 16 19:10:58 matteo dhclient: DHCPREQUEST of 10.192.9.23 on eth1 to 10.192.0.1 port 67
Oct 16 19:10:58 matteo dhclient: DHCPACK of 10.192.9.23 from 10.192.0.1
Oct 16 19:10:58 matteo dhclient: bound to 10.192.9.23 -- renewal in 241 seconds.
Oct 16 19:14:59 matteo dhclient: DHCPREQUEST of 10.192.9.23 on eth1 to 10.192.0.1 port 67
Oct 16 19:14:59 matteo dhclient: DHCPACK of 10.192.9.23 from 10.192.0.1
Oct 16 19:14:59 matteo dhclient: bound to 10.192.9.23 -- renewal in 275 seconds.
Oct 16 19:17:01 matteo CRON[4501]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 16 19:19:34 matteo dhclient: DHCPREQUEST of 10.192.9.23 on eth1 to 10.192.0.1 port 67
Oct 16 19:19:34 matteo dhclient: DHCPACK of 10.192.9.23 from 10.192.0.1
Oct 16 19:19:34 matteo dhclient: bound to 10.192.9.23 -- renewal in 299 seconds.
Oct 16 19:24:33 matteo dhclient: DHCPREQUEST of 10.192.9.23 on eth1 to 10.192.0.1 port 67
Oct 16 19:24:33 matteo dhclient: DHCPACK of 10.192.9.23 from 10.192.0.1
Oct 16 19:24:33 matteo dhclient: bound to 10.192.9.23 -- renewal in 293 seconds.
Oct 16 19:29:25 matteo dhclient: DHCPREQUEST of 10.192.9.23 on eth1 to 10.192.0.1 port 67
Oct 16 19:29:26 matteo dhclient: DHCPACK of 10.192.9.23 from 10.192.0.1
Oct 16 19:29:26 matteo dhclient: bound to 10.192.9.23 -- renewal in 283 seconds.
Oct 16 19:34:09 matteo dhclient: DHCPREQUEST of 10.192.9.23 on eth1 to 10.192.0.1 port 67
Oct 16 19:34:09 matteo dhclient: DHCPACK of 10.192.9.23 from 10.192.0.1
Oct 16 19:34:09 matteo dhclient: bound to 10.192.9.23 -- renewal in 270 seconds.

```

---

### Post by Enucatl on 2011-10-17
I just discovered my dhcp.leases files ask for a 600 seconds lease. I was unable to change that though. Any tips?

---

### Post by nocnokneo on 2011-11-06
same problem for me. any solutions? launchpad bug report?

---

