---
title: "problem assigning a static IP to a LAMP/SSH server?"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by pythonscript on 2010-07-17
I'm trying to set up a server to have one network card using DHCP, and the other using a static IP, but when I run:
```
sudo /etc/init.d/networking restart
``` to bring up the network interfaces, I get an error:

```

SIOCADDRT: No such process
Failed to bring up eth1

```Here's my network interface file from that system:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    address 192.168.1.205
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.1.255
    gateway 192.168.0.1

```Here's the part that's throwing me off. I have another server in my apartment, with *identical hardware and an identical installation of an Ubuntu LAMP/SSH server*, with an identical configuration file. The only change in that config file is that the static IP address if 192.168.1.200, instead of 192.168.1.205. 
I also have a third server using IP address 192.168.1.210, and it's working flawlessly as well. All of these are basic installations of Ubuntu server, all the default options, and selecting both LAMP and SSH packages to install. 

Any ideas what I can do to fix this? I've tried using other static IPs, too, and no luck.

EDIT:  After bringing the rest of my servers online, all 8 are working, *except this one*. Once again, identical hardware, identical LAMP/SSH configurations, etc, so it's just this server that's failing. I'm at a loss.

---

### Post by Iowan on 2010-07-17
> **pythonscript said:**
> 
```

auto eth1
iface eth1 inet static
    address 192.168.[COLOR="Red"]1[/COLOR].205
    netmask [COLOR="Red"]255.255.255.0[/COLOR]
    network 192.168.[COLOR="Red"]0[/COLOR].0
    broadcast 192.168.[COLOR="Red"]1[/COLOR].255
    gateway 192.168.[COLOR="Red"]0[/COLOR].1

```
The address, subnet, and network don't match. Network and broadcast are optional, but which subnet are you trying to use - 192.168.1.X or 192.168.0.X?

---

### Post by pythonscript on 2010-07-17
I'm trying to use the 192.168.1.X subnet. If I change my interfaces to this:

```

auto eth1
iface eth1 inet static
    address 192.168.1.200
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

```

is that the appropriate configuration?

---

### Post by Iowan on 2010-07-18
It *looks* OK, now if it works...

---

### Post by pythonscript on 2010-07-18
It is working now, and I've changed all my servers accordingly. Thank you for the help.

---

