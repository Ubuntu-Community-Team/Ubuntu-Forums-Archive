---
title: "Virtual Network Interface"
date: 2009-07-31
forum: Networking &amp; Wireless
---

### Post by mthalis on 2009-07-31
In Ubuntu 9.04 how can I create virtual network interface? Below show my current network configuration

**interfaces**

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.101.232
	netmask 255.255.255.0
	network 192.168.101.0
	broadcast 192.168.101.255
	gateway 192.168.101.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 203.115.0.1
	dns-search itess.lk

auto eth1
iface eth1 inet static
	address 192.168.20.254
	netmask 255.255.255.0
	network 192.168.20.0
	broadcast 192.168.20.255

```

---

### Post by martinbaselier on 2009-07-31
**man interfaces** 
will show you the documentation. 
I don't know what you're wanting to do exactly. Also if you're planning to use interfaces to set up your network, you should disable the networkmanager as it has its own methods for connecting and your changes in interfaces won't have effect.

---

### Post by mthalis on 2009-07-31
Thank reply searching net i found this
[http://ubuntuforums.org/showthread.php?t=555319](http://ubuntuforums.org/showthread.php?t=555319)

I don't you understand my question or not 

Using dhcp server can i create virtual network?

---

### Post by mthalis on 2009-07-31
New setting

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.101.232
	netmask 255.255.255.0
	network 192.168.101.0
	broadcast 192.168.101.255
	gateway 192.168.101.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 203.115.0.1
	dns-search itess.lk
	hwaddress ether 00:1e:0b:af:58:ae

auto eth1
iface eth1 inet static
	address 192.168.20.254
	netmask 255.255.255.0
	network 192.168.20.0
	broadcast 192.168.20.255
	hwaddress ether 00:19:e0:0b:5b:49

auto eth1:1
iface eth1:1 inet static
	address 192.168.20.240
	netmask 255.255.255.0
	network 192.168.20.0
	broadcast 192.168.20.255
	hwaddress ether 00:19:e0:0b:5b:49

```

After restarting Network follow error display

```

 * Deconfiguring network interfaces...                                   [ OK ] 
ites@gateway:~$ sudo /etc/init.d/networking start
 * Configuring network interfaces...                                             
* if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts
 * if-up.d/mountnfs[eth0]: waiting for interface eth1:1 before doing NFS mounts
 * if-up.d/mountnfs[eth1]: waiting for interface eth1:1 before doing NFS mounts
SIOCSIFHWADDR: Device or resource busy - you may need to down the interface
Failed to bring up eth1:1.


```

---

### Post by mthalis on 2009-08-01
Is it posible to assign virtual network interface for remote machine(windows or linux)?

waiting for you're comments.

---

