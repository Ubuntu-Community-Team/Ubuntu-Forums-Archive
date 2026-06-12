---
title: "Static IP configuration issues"
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by Enforcer83 on 2011-10-15
I am having problems configuring my Ubuntu 11.10 distribution to use a static IP.  I installed from the alternate disk and shortly after installation of several components, including ethtool, synaptic, vim, LAMP, Samba, and CUPS servers and several reboots,  my computer would no longer connect to the internet using the static IP I specified during installation.

the following comes from my /etc/network/interfaces file

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.3
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
```

I have a gigabit router to which my xbox, blu-ray player, and desktop (running ubuntu and the computer I am having problems with) are all connected,  How do I get my desktop to default to a gigabit connection vice a 100Mb/s connection?

---

