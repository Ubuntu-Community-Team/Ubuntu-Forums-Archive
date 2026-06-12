---
title: "dhcpd3 server not starting on startup"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by Relived on 2010-05-31
Hey guys,
I currently got Ubuntu 10.0.4 server edition running on my server.
I got 2 network cards in it. One for (eth0) the pppoe connection and the other one (eth1) for dhcp and network.

When i installed dhcpd3 server a couple of days ago, it wouldn't start.
So i searched the web and came on the conclusion that i have to do
" sudo ifconfig eth1 down
sudo ifconfig eth1 up 192.168.0.1"

Problem is i don't have connection with this pc all the time. So if i have to restart it, the dhcp server won't start. Is there a way to fix this problem?

Thanks

Relived.

---

### Post by suseendran.rengabashyam on 2010-06-01
Hi,

The 'dhcp3-server' by default needs to listen on a particular network interface, in your case it is 'eth1' so in the file /etc/default/dhcp3-server you need to have the following configuration

```
INTERFACES="eth1"
```

You can refer this documentation [https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server) for configuring /etc/dhcp3/dhcpd.conf file.

Hope this helps.

---

