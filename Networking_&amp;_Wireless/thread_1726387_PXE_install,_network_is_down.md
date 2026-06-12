---
title: "PXE install, network is down"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by richard_wu0313 on 2011-04-11
hi all,
when installing ubuntu by PXE, the net card could get PXE menu and then got IP address, however, later the network would down, and can't get IP address. if you plug in another net card, the net card could get IP address. only the net card which connect to PXE network couldn't get IP address.

message from /var/log/syslog

dhclient: receive_packet failed on eth0: Network is down
kernel: [18.583687] tg3 0000:00:14.6 eth0 Link is down
there is already a pid file /var/run/dhclient.pid wi pid 1356

ubuntu 10.10 x86_64

---

