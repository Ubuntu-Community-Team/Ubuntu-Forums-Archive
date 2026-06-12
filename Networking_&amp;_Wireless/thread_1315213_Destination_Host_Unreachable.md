---
title: "Destination Host Unreachable"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by guitar_man on 2009-11-05
hello..
I have a problem

When I ping other computer on my network it unreachable when there is no user log-in the GDM...
Can anyone help me or is this normal?

---

### Post by guitar_man on 2009-11-05
anyone??

---

### Post by guitar_man on 2009-11-05
hello..
I have a problem

When I ping other computer on my network it unreachable when there is no user log-in the GDM...
Can anyone help me or is this normal?

---

### Post by wulfgang on 2009-11-05
This is normal, well. It does same thing to me.

---

### Post by guitar_man on 2009-11-05
Can I connect through it via SSH without any user logged in the host....

---

### Post by sprouty on 2009-11-05
are you using server?

if you are in /etc/network/interfaces

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.10.10.150
	netmask 255.255.255.0
	network 10.10.10.0
	broadcast 10.10.10.255
	gateway 10.10.10.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 10.10.10.1
```

---

### Post by guitar_man on 2009-11-05
I'm not using a server...
here is my /etc/network/interfaces

> auto lo
iface lo inet auto


---

### Post by doas777 on 2009-11-05
thats the problem.

the network manager in gnome only sets up your network at login (so you can select differnt wifi nets or whatever).

if you want to run services off the box (samba, sshd, etc) you have to configure the properties in system-space via /etc/network/interfaces (using either dhcp or static addressing)

here is a quick guide:
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

if you have a dns server, then you want to add lines to your /etc/resolv.conf
```
domain <dnsdomainname>
search <dnsdomainname>
nameserver <dns server ip>
nameserver <other dns server ip>

```

---

### Post by redmk2 on 2009-11-05
> **guitar_man said:**
> I'm not using a server...
here is my /etc/network/interfaces

It is due tho the interface being managed by ***network manager***.  The manager can't select the config until it knows who is logged in.

If you want the interface to be up before anyone logs in (the traditional condition) you need to configure the interface manually and provide a static IP address.

Edit:  As doas777 has just said.  :D

---

### Post by guitar_man on 2009-11-05
should I set the unterface loopback or auto?

---

### Post by doas777 on 2009-11-05
ok,
if you have a network card, you always have at least 2 interfaces listed: the physical nic, and the loopback. you want to configure the nic, not the loopback, so leave interface lo alone.

first you need to find the name of your interface. it is usually eth0, eth1, etc.
login and run 
```
ifconfig
``` to list your interfaces. look for the one with an ipaddress as that is likely the one you want. 

lets assume that your interface is eth0. if you wanted to set the interface for DHCP, then use this:
```

auto lo
iface lo inet auto 			 		

auto eth0
iface eth0 inet dhcp

```

now if you want a static IP of 192.168.100.2 and your gateway address is 192.168.100.1
then you want to use this:
```

auto lo
 iface lo inet auto 			 		

auto eth0
iface eth0 inet static
address 192.168.100.2
netmask 255.255.255.0
gateway 192.168.100.1

```

---

### Post by redmk2 on 2009-11-05
> **guitar_man said:**
> should I set the unterface loopback or auto?

Ang sagot sa iyong tanong...neither.  

The loopback is as doas777 stated (e.g. the internal interface).  The *auto* that you refer to tells the specific interface to automatically come up upon booting.

Once again, as doas777 stated, use the physical interface on the NIC (usually designated eth0, eth1, etc.)

---

### Post by Iowan on 2009-11-05
On newer (Ubuntu) systems, Network Manager doesn't set up internet until a user logs in.  On Jaunty (at least), an interface configured via */etc/network/interfaces* activated on machine boot. On my older Gutsy-class machines - all network configuration was via the interfaces file.

---

### Post by cariboo on 2009-11-05
Please don't double post, I have merged your two threads

---

### Post by guitar_man on 2009-11-06
> **cariboo907 said:**
> Please don't double post, I have merged your two threads

forgive me.[-o<


Thank you everyone for the help.;)[-o<

---

