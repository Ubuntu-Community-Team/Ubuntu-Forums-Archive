---
title: "Unable to configure a transparent bridge"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2011-06-18
Hi everyone,

I'm a college student and we are assigned dynamic IPs through a dhcp server. I have one NIC on my desktop but I want to get two IPs through bridging.

In order to make it work, I created a bridge and just for the sake of two virtual interfaces, I create a tap0 interface along with the default eth0 and used the following configuration in /etc/network/interfaces file.

```
auto eth0
iface eth0 inet dhcp

auto br0
iface br0 inet manual
        bridge_ports eth0 tap0
        bridge_stp on
        bridge_fd 0
        bridge_maxwait 0

auto tap0
iface tap0 inet dhcp

```

When I restart the network after doing this, I don't receive any DHCP offers for the IP. A tcpdump on the interface br0 shows that it can see all the traffic on the wire but for some reason none of the two interfaces manage to get an address. Any suggestions?

---

