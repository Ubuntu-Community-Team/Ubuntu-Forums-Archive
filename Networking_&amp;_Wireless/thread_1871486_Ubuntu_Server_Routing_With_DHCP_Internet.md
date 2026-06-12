---
title: "Ubuntu Server Routing With DHCP Internet"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by Halfbrazilian on 2011-10-29
Hello. I have set up a router using Ubuntu Server 11.10. When I setup the second interface (intranet) and restarted the server, I could not connect to the internet. Turned out that the server was using my secondary interface (intranet) as the default gateway instead of my primary interface (internet). I temporarily remedied the situation using:

```

sudo route del default
sudo route add default gw 24.216.160.1 metric 100 dev eth1

```

I could put these command in /etc/network/interfaces but the problem is that I would have to hard code the IP address of the network gateway even though my ISP assigns IP addresses via DHCP.

My question is this: what process decides the default routing tables in Ubuntu Server? Can I mark an interface as the primary interface and have the routing tables automatically pick the correct default gateway/ip address? I have provided my /etc/network/interfaces below.

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

# The wired network interface
auto eth0
iface eth0 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1

```

Any help will be appreciated.

---

