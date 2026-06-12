---
title: "Sharing Internet Connection Through Multihomed Computer"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by nirvana21 on 2010-12-02
I am in college and live in a dorm room. As a dorm resident, I have access to only one wired network connection and I am not allowed to connect it to a router. My primary computer is multihomed and I was hoping I could share network access (eth1) through eth0 to a router. Then I want to hook up my secondary system to the router. I am not using the WAN port on the router. I believe this makes it act like a switch, which seems to be what I want.


Here is my /etc/network/interfaces file on my primary computer
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1

#I added
iface eth1 inet dhcp


iface eth0 inet static
address 192.168.1.2
network 192.168.1.0
netmask 255.255.255.0
gateway 192.168.1.1

```
eth1 is my network connection
eth0 is what I want to share through
router's address is 192.168.1.1

---

### Post by nirvana21 on 2010-12-03
I have been doing some more research. I can now sucessfully connect to my secondary system from my first while maintaining network access. It is not automatic however. I have to use this command to get a connection with my secondary system:

```
sudo /sbin/ifconfig eth0 192.168.1.10 netmask 255.255.255.0 broadcast 192.168.1.255
```

How can I make this automatic?

My other problem is that although I can connect to the secondary system, it cannot get an Internet connection. How can I share the connection through my primary system?

---

### Post by nirvana21 on 2010-12-05
I saw some information on iptables forwarding. If I forward eth0, can my primary system still communicate with the secondary one?

---

