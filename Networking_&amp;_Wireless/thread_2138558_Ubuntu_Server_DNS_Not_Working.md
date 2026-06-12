---
title: "Ubuntu Server DNS Not Working"
date: 2013-04-24
forum: Networking &amp; Wireless
---

### Post by JamesKraw on 2013-04-24
I'm trying to configure a home server using Ubuntu 12.10. 

I've setup static ip in ```
/etc/network/interfaces
``` and remove the DHCP client some other information I found however I'm having trouble finding how to configure DNS settings. 

I've had a look at ```
/etc/resolv.conf
``` but that has the line about being overridden and the changes don't stick. I've also added the line ```
dns-nameservers 8.8.8.8 8.8.4.4
``` to my ```
/etc/network/interfaces
``` file under the eth0 settings so it looks like this, 

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address  10.13.23.211
netmask 255.255.255.0
network 10.13.23.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 8.8.8.8 8.8.4.4

```

But whenever I try to connect to an outside source, for instance, with ping I get the following error, ```
ping: unknown host www.google.com
```

---

### Post by ahallubuntu on 2013-04-24
~

---

### Post by JamesKraw on 2013-04-24
I've corrected the two different subnets now. It should have been 10.13.23.1/24 but was just typo'd from a copy/paste. And the only reason it isn't being setup via router is because of habit. I used to run a openSuSe server and for years configured that manually. I probably could configure via router but would still like to know why it isn't working manually.

New /etc/network/interfaces looks like this

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address  10.13.23.211
netmask 255.255.255.0
network 10.13.23.0
broadcast 10.13.23.255
gateway 10.13.23.1
dns-nameservers 8.8.8.8 8.8.4.4

```

---

### Post by Doug S on 2013-04-24
Looks O.K. to me, and the information should be used to create /etc/resolv.conf . So what are the contents of /etc/resolv.conf ?

---

