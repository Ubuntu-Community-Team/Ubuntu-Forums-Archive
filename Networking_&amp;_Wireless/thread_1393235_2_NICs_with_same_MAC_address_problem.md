---
title: "2 NICs with same MAC address problem"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by mdewet on 2010-01-29
Hi All,

I have 2 NICs in my U9.04 Server box (eth0, eth1).  After I added 2 virtual interfaces for each physical interface (eth0:1,eth0:2,eth1:1,eth1:2), the MAC addresses of all the interfaces have changed to that of eth0.  Because eth1 was configured to be on my local network, I can't access the box remotely anymore.

Even after I added the MAC addresses to the /etc/network/interfaces file, it still shows only 1 MAC address for all interfaces.

This is the configuration

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
iface eth0 inet static
        address 192.168.40.156
        hwaddress ether aa:00:04:00:0a:04
        netmask 255.255.255.0
        gateway 192.168.40.150

iface eth0:1 inet static
        address 10.0.1.1
        netmask 255.255.255.0
        gateway 192.168.40.150

iface eth0:2 inet static
        address 10.0.2.1
        netmask 255.255.255.0
        gateway 192.168.40.150


# The additional network interface
auto eth1
iface eth1 inet static
        address 192.168.30.129
        hwaddress ether 00:30:bd:b9:f6:81
        netmask 255.255.255.0

auto eth1:1
iface eth1:1 inet static
        address 10.1.0.1
        netmask 255.255.255.0

auto eth1:2
iface eth1:2 inet static
        address 10.2.0.1
        netmask 255.255.255.0

```


Did my second NIC (eth1) suddenly give in?

Can someone please explain what is happening here.

Thank you
mdewet

EDIT:

I found that the reason for not being able to connect was actually because the IP address for eth1 also wasn't configured at start-up, even though it is in the configuration file.

---

### Post by mdewet on 2010-02-01
I found the solution just now in the place where I should have started 3 days ago.  I placed the extra NIC in another PCI slot, and everything was fixed.  

This is the /etc/network/interfaces file for setting up multiple logical interfaces on multiple NICs

```

# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth1
iface eth1 inet static
        address 192.168.30.129
        netmask 255.255.255.0

auto eth1:1
iface eth1:1 inet static
        address 10.0.10.1
        netmask 255.255.255.224

auto eth1:2
iface eth1:2 inet static
        address 10.0.20.1
        netmask 255.255.255.0

# The secondary network interface
auto eth0
iface eth0 inet static
        address 192.168.40.156
        netmask 255.255.255.0

auto eth0:1
iface eth0:1 inet static
        address 10.10.0.1
        netmask 255.255.255.0

auto eth0:2
iface eth0:2 inet static
        address 10.20.0.1
        netmask 255.255.255.0

```

---

