---
title: "Two interfaces with static ip, strange eth1-eth0 inteface"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by jegumi on 2011-07-29
I have two static network interfaces with this configuration:

/etc/network/interfaces

iface eth0 inet static
address 10.X....
netmask 255.255.255.0
network 10.X..X.0

iface eth0 inet static
address 192.X...
netmask 255.255.255.0
network 192.X.X.0
gateway 192.X.X.1

/etc/resolv.conf

nameserver 192.168.2.1

Sometimes my netwoks work fine, but other the system create a new interface called eth1-eth0 instead of eth0

In /var/log/syslog I can see an error from udev when try to rename eth1-eth0 to eth0

In /etc/udev/rules.d/70-persistent-net.rules my interfaces are defined correctly.

And the worse is that the error appears randomly, each two or three reboots.

Any idea??

---

