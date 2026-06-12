---
title: "Server 11.04, One NIC stops working"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by asqde on 2011-07-25
Hi, I've got strange networking problem.

Ubuntu Server 11.04 upgraded from 10.04 or 10.10 can't remember.
Two network interfaces: eth0 - public (dhcp), eth1 - private (static).
After working perfect for week or two eth0 loses its settings and doesn't want to reconfigure again. Neither ifdown/ifup, nor /etc/init.d/networking restart helps.
The only solution I've found so far is reboot.

ifup eth0 hangs for one minute. Prints: ssh stop/waiting|ssh start/running, process 5325
dhclient eth0 also hangs for minute and prints nothing. Same for dhclient3 eth0.

Got this problem for couple of weeks maybe month or two.
No settings/configurations changed recently.
Install all updates every time I login.
Running: ufw, pptpd (eth0 -> eth1), samba, vsftpd, apache, mysql

Any ideas?

Edit: DHCP lease time is 10 minutes.

---

