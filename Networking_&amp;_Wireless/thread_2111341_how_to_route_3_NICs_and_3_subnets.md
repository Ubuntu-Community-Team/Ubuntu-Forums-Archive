---
title: "how to route 3 NICs and 3 subnets"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by msurkan on 2013-02-01
I am trying to setup routing between 3 subnets using an Ubuntu 12.10 server with 3 NICs. I would like to be able to have all these subnets route between one another as well as be able to access the internet.

The 10.0.2.0 network is connected to the internet. The Netgear router box connected to the Internet has an address of 10.0.2.1.

The three subnets are 10.0.2.0/16, 10.100.0.0/16, and 10.101.0.0/16.

I have tried to setup my /etc/network/interfaces to define both the NICs and the routing but it doesn't seem to be working. I can ping all the NICs on the ubuntu server from any machine on any of the respective subnets but I am not able to ping any systems on different subnets from any of those subnets. Neither can I get out to the internet from the subnets.

```
# /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# eth0
auto eth0
allow-hotplug eth0
iface eth0 inet static
        address 10.0.2.154
        netmask 255.255.0.0
        gateway 10.0.2.1
        dns-nameservers 10.0.2.100 8.8.8.8

# eth1
auto eth1
allow-hotplug eth1
iface eth1 inet static
        address 10.100.0.4
        netmask 255.255.0.0
        dns-nameservers 10.0.2.100 8.8.8.8

# eth2
auto eth2
allow-hotplug eth2
iface eth2 inet static
        address 10.101.0.1
        netmask 255.255.0.0
        dns-nameservers 10.0.2.100 8.8.8.8

up route add -net 10.0.0.0 netmask 255.255.0.0 gw 10.0.2.1 dev eth0
up route add -net 10.100.0.0 netmask 255.255.0.0 gw 10.0.2.154 dev eth0
up route add -net 10.101.0.0 netmask 255.255.0.0 gw 10.0.2.154 dev eth0
up route add -net 10.101.0.0 netmask 255.255.0.0 gw 10.100.0.4 dev eth1
up route add -net 10.0.0.0 netmask 255.255.0.0 gw 10.100.0.4 dev eth1
up route add -net 10.100.0.0 netmask 255.255.0.0 gw 10.101.0.1 dev eth2
up route add -net 10.0.0.0 netmask 255.255.0.0 gw 10.101.0.1 dev eth2

```

I would love to hear any suggestions as to how I could fix my /etc/network/interfaces file to properly route between these subnets.

---

### Post by msurkan on 2013-02-01
Ok. I have figured out to get routing working between all three subnets. I just had to remove all the routes and gateway definitions I had in my /etc/network/interfaces file. I also enabled IPv4 forwarding with net.ipv4.ip_forward=1.

My problem now is that I can't route out to the internet from any of these subnets. When I try adding a gateway to my eth0, to point to the external internet router, the subnet attached to eth0 (my 10.0.0.0 subnet) becomes unroutable.

---

### Post by SeijiSensei on 2013-02-01
First, I don't understand why you have each subnet listed twice in the routing tables above.  Moreover, you are using /16 subnet masks when I suspect you really want /24's (i.e., a netmask of 255.255.255.0).  Linux will automatically set up routes to the various networks when the interfaces come up.  You shouldn't need to declare any of them manually except the default gateway, 10.0.2.1.
```
route add default gw 10.0.2.1
```
should be all it takes.  That may also happen automatically based on the gateway parameter in the interfaces file.

If you want to forward all default traffic out to the Internet, you'll need a masquerading rule using iptables. Something like:

```
sudo iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 10.0.2.154
```

That tells the kernel that all packets going out to the default gateway via eth0 should be rewritten with the source address assigned to eth0, 10.0.2.154.  The kernel will keep track making sure return packets are routed back to their original source IPs.

---

### Post by msurkan on 2013-02-02
Thanks! The iptables command to forward traffic out to the internet  was the final piece of the puzzle!

---

### Post by msurkan on 2013-02-02
For everyone's reference here is the final solution to my routing problem. Below you will find the final /etc/network/interfaces, /etc/iptables.rules and /etc/sysctl.d/10-routing.conf files I ended up with.

It turns out that I needed to remove the routing commands from my /etc/network/interfaces file and then setup ipforwarding.

=========================================
/etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# eth0
auto eth0
allow-hotplug eth0
iface eth0 inet static
        address 10.0.2.154
        netmask 255.255.0.0
        gateway 10.0.2.1
        dns-nameservers 10.0.2.100 8.8.8.8
        pre-up iptables-restore < /etc/iptables.rules

# eth1
auto eth1
allow-hotplug eth1
iface eth1 inet static
        address 10.100.0.4
        netmask 255.255.0.0
        dns-nameservers 10.0.2.100 8.8.8.8

# eth2
auto eth2
allow-hotplug eth2
iface eth2 inet static
        address 10.101.0.1
        netmask 255.255.0.0
        dns-nameservers 10.0.2.100 8.8.8.8

=================================================

/etc/iptables.rules

# Generated by iptables-save v1.4.12 on Fri Feb  1 20:43:36 2013
*nat
:PREROUTING ACCEPT [204:18924]
:INPUT ACCEPT [35:6098]
:OUTPUT ACCEPT [3:164]
:POSTROUTING ACCEPT [1:40]
-A POSTROUTING -o eth0 -j SNAT --to-source 10.0.2.154
COMMIT
# Completed on Fri Feb  1 20:43:36 2013

=================================================

/etc/sysctl.d/10-routing.conf

net.ipv4.ip_forward=1

---

