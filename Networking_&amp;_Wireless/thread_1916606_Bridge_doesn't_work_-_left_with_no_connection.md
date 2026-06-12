---
title: "Bridge doesn't work - left with no connection"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by c-m on 2012-01-28
Hi,

I'm trying to set up a bridge so that I can use my main ubuntu box as an openvpn server.

I have amended my /etc/network/interfaces to look like this:


```

auto lo
iface lo inet loopback

# Set up the bridge interface for OpenVPN
auto br0
iface br0 inet static
address 192.168.0.100
network 192.168.0.0
netmask 255.255.255.0
gateway 192.168.0.1
bridge_ports eth1
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off



iface eth1 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down


```

Then ran sudo /etc/init.d/networking restart

The problem is, when eth1 then connects to the router, I can't get any internet connection at all, nor can I browse my local network.

```
$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          device eth1 is not a slave of br0

Waiting for br0 to get ready (MAXWAIT is 20 seconds).
ssh stop/waiting
ssh start/running, process 9340
                                                                         [ OK ]


```

---

