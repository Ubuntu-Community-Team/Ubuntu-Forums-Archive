---
title: "pppoe connection on boot"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by franconob_pr on 2009-08-15
Hello everybody, I have a problem with mi ppp connection when I boot up the computer. 
I have 2 network adapters:
[LIST=1]
[*]eth0 witch connects to an ethernet modem (Cisco 667)
[*]eth1 witch connects to the internal network (Switch)
[/LIST]
This PC is acting as a router with address 10.0.0.1 on eth1
I have configured the ppp connnection via pppoeconf and everything seems to be ok.
I can connect using 'pon dsl-provider'.
The problem is when I reboot the computer. I get eth0 and eth1 up, alog with ppp0 with the public ip. The connection seems to be OK, but I can't ping anywhere outside my net (e.g 'ping google.com')
I have to 'poff' and then 'pon dsl-provider' to get internet. I'ts a strange behavior and I don't know what's happening.
I attach the /etc/network/interfaces file

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#local net
auto eth1
iface eth1 inet static
address 10.0.0.1
netmask 255.0.0.0
broadcast 10.0.0.255

# The primary network interface
auto eth0

auto dsl-provider
iface dsl-provider inet ppp
#pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
pre-up iptables-restore < /etc/iptables.up.rules
provider dsl-provider


If you need more information just tell me.

Thanks in advance.

Sorry for my English, I'm from Argentina.

---

### Post by superprash2003 on 2009-08-15
you could enter your DSL username and password in your ethernet modem and avoid the pon and poff in ubuntu..

---

### Post by franconob_pr on 2009-08-17
I can't because i have a Cisco 667 witch does not have a web intrerface. I need the ppp dialer

---

