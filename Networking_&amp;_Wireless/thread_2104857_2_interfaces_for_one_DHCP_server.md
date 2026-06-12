---
title: "2 interfaces for one DHCP server"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by VaultDweller13 on 2013-01-14
Hi, help please giving DHCP two NICs for address leasing.
Ubuntu 12.04

I have eth0, wich is my ISP
And i want eth1 & eth2 to serve DHCP

How to configure interfaces?
Does that means that i will have two gateways?

I tried like this but no luck...

```

auto eth0
iface eth0 inet static
        address xxx.xxx.xxx.xxx
        netmask xxx.xxx.xxx.xxx
        network xxx.xxx.xxx.xxx
        broadcast xxx.xxx.xxx.xxx
        gateway xxx.xxx.xxx.xxx
        dns-nameservers xxx.xxx.xxx.xxx

auto eth1
iface eth1 inet static
        address 192.168.1.1
        netmask 255.255.255.0

auto eth2
iface eth2 inet static
        address 192.168.2.1
        netmask 255.255.255.0


```

```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1 eth2"

```

```

# A slightly different configuration for an internal subnet.
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.10 192.168.1.254;
  option routers 192.168.1.1, 192.168.2.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 3600;
  max-lease-time 7200;
}

```

Thanx)

---

### Post by jonobr on 2013-01-14
Hello


I notice that your two internal ethernet interfaces are on the same subnet,.
Is that intentional?
You define your default gateway in two separate subnets, is that correct?
> 
option routers 192.168.1.1, 192.168.2.1;

If all the devices are in the same subnet, would you not just have everything on the eth1 interface?
If your using the same subnet on two different interfaces, that is acting more like a switch then a router,

---

### Post by VaultDweller13 on 2013-01-14
> **jonobr said:**
> Hello


I notice that your two internal ethernet interfaces are on the same subnet,.
Is that intentional?
You define your default gateway in two separate subnets, is that correct?


If all the devices are in the same subnet, would you not just have everything on the eth1 interface?
If your using the same subnet on two different interfaces, that is acting more like a switch then a router,

Ok 2 subnets, not a problem.
How to correctly write configs in interfaces and dhcpd.conf

---

### Post by jonobr on 2013-01-14
[This]("https://help.ubuntu.com/community/dhcp3-server") should contain what you need ,

In There is a multi interface example.

---

