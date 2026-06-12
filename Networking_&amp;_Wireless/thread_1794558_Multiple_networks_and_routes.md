---
title: "Multiple networks and routes"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by povlhp on 2011-07-01
I have some issues with a server running syslog-ng. I have disabled the firewall.

I have 2 network interfaces connected to 2 different subnets on a big LAN.
I receive syslog events on eth0, and I want to make sure responses to packets coming in that way goes out the same way. Network firewall in front allows only incoming syslog traffic. 

eth1 is the Interface I would like to make my default gateway, as that IP address has network access to other parts of the network.

If eth0 is my default gateway, syslog-ng works fine. 

If I make the default route via the gateway on the eth1 network, then I will not get syslog entries. They are seen on eth0 using tcpdump, so they will reach the ip-stack. But they disappear.

This /etc/network/interfaces causes syslog events to not arrive. If I change so that the other interface has the gateway everything works fine. Any suggestion on what is wrong ?

```
auto eth0
iface eth0 inet static
        address 10.215.255.254
        netmask 255.255.255.0
#       gateway 10.215.255.1
        post-up ip route add 10.215.255.1/32 dev eth1 src 10.215.255.254


auto eth1
iface eth1 inet static
        address 10.216.36.254
        netmask 255.255.255.0
        gateway 10.216.36.1
        post-up ip route add 10.216.36.1/32 dev eth1 src 10.216.36.254

```Since Linux per default is stupid, and likes to send out packets on one interface with a source address other, I have been trying iproute2 options, to have a different routing table for traffic coming from eth0 aka 10.215.255.254. Adding the below lines in /etc/network/interfaces, and setting the default gw on eth1 instead, but then syslog is not working again.

```
       post-up ip route add default via 10.215.255.1 table T0
       post-up ip rule add from 10.215.255.254 table T0
```If I netcat w/ tcp or udp to the eth0 IP address from the host itself, when syslog is not logged (i.e. gw on eth1), then things are logged (with a source address of the 10.215.255.254 address).

I remember I had the problem once before, but can't remember how I solved it.

So for now, the machine has limited network access, and can only use the proxy on the eth1 network to access stuff.

---

