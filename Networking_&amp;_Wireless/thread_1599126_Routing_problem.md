---
title: "Routing problem"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by GerhardWessels on 2010-10-17
Hi All,

I have a server with 4 NICs that is running Proxmox (Ubuntu 10.04). My idea is to install Shorewall on the host machine with the regulation $FW/net/loc/dmz zone configuration (the 4th NIC will be in loc2 zone - later...).

I am not clear as to what should be working prior to installing Shorewall regarding routing. In other words, should I be able to get Internet access on machines connected to eth1 and eth2 BEFORE I install Shorewall or will Shorewall take care of that for me?

I am connected to the Internet through an ADSL router with an internal IP of 10.0.0.2. I have configured the DHCP on the router  to issue an address of 10.0.0.106 to eth0 (I checked the MAC) on the server. I have Internet access from the server itself (host).

Here is my /etc/network/interfaces file:

```

# network interface settings
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address   10.0.0.106
	netmask   255.255.255.0
	gateway   10.0.0.2
	network   10.0.0.0

auto eth1
iface eth1 inet static
	address   192.168.1.254
	netmask   255.255.255.0
        network   192.168.1.0
        broadcast 192.168.1.255

auto eth2
iface eth2 inet static
	address   192.168.2.254
	netmask   255.255.255.0
        network   192.168.2.0
        broadcast 192.168.2.255

```

Here is the result of "ip route ls"

```

10.0.0.0/24 dev eth0  proto kernel  scope link  src 10.0.0.106
192.168.2.0/24 dev eth2  proto kernel  scope link  src 192.168.2.254
192.168.1.0/24 dev eth1  proto kernel  scope link  src 192.168.1.254
default via 10.0.0.2 dev eth0

```

With this setup I am not able to connect to the internet with a machine that is directly connected to either eth1 or eth2 with cross link cables and with static IPs in the correct subnet, e.g. 192.168.1.1

Again I am not sure if this is something Shorewall should be taking care of. I suspect not because I have installed Shorewall and did the whole three-interfaces setup but I did not get Internet connectivity from the loc and dmz zones.

I am sure this has been asked and answered before but I can't find it.

I'd appreciate help to get this going.

---

### Post by GerhardWessels on 2010-10-18
Anyone?

---

### Post by GerhardWessels on 2010-10-18
For those who care, the answer is "Shorewall takes care of it".

My setup did not work because I did not set the machines' in the loc and dmz zones DNS to point to the ADSL router address.

---

