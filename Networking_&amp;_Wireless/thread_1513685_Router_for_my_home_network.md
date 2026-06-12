---
title: "Router for my home network"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by terbor on 2010-06-19
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

I followed these instructions but am not able to get my computers behind the router to see the Internet.  I am able to ping the router, but not to the Internet, pinging google using both the name and IP.  So I am stumped.  My router can get to the Internet fine.  Here are my files.
  Thanks for any help
**Router**
*_Resolv.conf_*
```
cat /etc/resolv.conf 
nameserver 192.168.0.1
```
_*Interfaces*_

```
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address xxx.xxx.xxx.xxx
	netmask xxx.xxx.xxx.xxx
	gateway xxx.xxx.xxx.xxx

auto eth1
iface eth1 inet static
	address 192.168.0.1
	netmask 255.255.255.0
```

**Computer behind router**
_*Resolv.conf*_
```
cat /etc/resolv.conf 
nameserver 192.168.0.1
```

_*Interfaces*_
```
cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0

iface eth0 inet static
	address 192.168.0.55
	netmask 255.255.255.0
	gateway 192.168.0.1
```

---

### Post by Iowan on 2010-06-21
Have you tried configuring the client via Network Manager rather than "interfaces"? Some threads suggest that "interfaces" only "appears" to work with new NM... though I've seen threads that sork this way, too...

---

### Post by Tpolich on 2010-06-21
Well first of all unless your running a DNS server on your router your never going to get anything.

change ```
nameserver 192.168.0.1
```
to googles dns server ```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

This also goes for your router as well.

Other than that I would make sure that your router has ```
cat /proc/sys/net/ipv4/ip_forward 
output 1
```
if it doesn't you need to ```
echo "1" >> /proc/sys/net/ipv4/ip_forward

```

also remember that they changes are temporary. You need to write them into a script for them to be there every time your restart. A good place to add them to is the end of /etc/rc.local

---

