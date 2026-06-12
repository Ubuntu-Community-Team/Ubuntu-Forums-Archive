---
title: "Specify gateway interface"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by bmcclint on 2013-04-22
I have 12.10 running with three network interfaces. One is my ISP(eth2), one my internal network(eth1) and the last for my HDHomeRun(eth0) tuner.

The system is a server/firewall for my internal network along with other services.

I am having trouble getting my ISP interface to be the default gateway. It seems to be setting one of the other interfaces eth0 or eth1. It was on eth1 for a while but then changed to eth0 and seems to be there consistently now. I can remedy the situation by removing the gateway route and adding a new route manually but would like a proper solution. What I have implemented is a reroute.sh on rc2.d/S99reroute. Solves the problem but seems like a hack.

What is the proper way to get the default gateway to set properly?
Specify which interface is the gateway interface?

Is it an order of operation in the interfaces file?

#/etc/network/interfaces
auto eth2
iface eth2 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.1.254
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255

auto eth0
iface eth0 inet static
address 192.168.2.254
network 192.168.2.0
netmask 255.255.255.0
broadcast 192.168.2.255

BTW: I did mess up NetworkManager sometime back when attempting to get the ethX names back. I got that working after much dilemma. I simply may just have the system jacked enough to be acting goofy.

Note: reroute.sh also setups ipv4 forwarding via iptables.

Bottom line, everything works with what I have setup. Ii just seems like a hack rather than a proper installation.

Any insight greatly appreciated.

---

### Post by Iowan on 2013-04-22
The **gateway** option in */etc/network/interfaces* should help. You might also need to set up a default route.
Network Manager and  */etc/network/interfaces* don't play nicely together. Most features can be configured either way.

---

### Post by bmcclint on 2013-04-25
> **Iowan said:**
> The **gateway** option in */etc/network/interfaces* should help. You might also need to set up a default route.
Network Manager and */etc/network/interfaces* don't play nicely together. Most features can be configured either way.

I cannot use a gateway option in interfaces unless there is a 'use interface X' way of specifying gateway.

eth2 is my ISP and that is my gateway.  It's via DHCP from ISP so I cannot hard set a gateway.

eth1/0 are internal interfaces and NOT gateways.

My suspision is the static interfaces setup first, the DHCP interface takes its time so the system decides on an gateway.

My reroute script is a hardcode to remove the incorret gateway and add the correct.

I suspect there is someway to make the system configure the correct interface as a gateway, the DHCP interface.

---

### Post by bmcclint on 2013-04-25
Maybe a thought...How to tell an interface it cannot have a gateway.

I see lots of examples of people setting gateways but my concern is the ISP.  They manage their network.  If their infrastructure changes I'd like to dynamically change with them.

My current solution worked as I only configured the ISP interface(eth2), rebooted and noted the gateway address.  Configured the remaining two interfaces(eth1/0) as defined above and created the reroute script to remove the default route, which ends up on one of the static interfaces(eth1/0), and add the ISP(eth2) gateway address.

This works until something upstream changes.  Then I have the honor of as needle in a hay stack search to determine what changed.

One would suspect there is a way to tell in interface, not knowing the IP, it will be the primary OR tell an interface in CANNOT be a gateway interface.

---

