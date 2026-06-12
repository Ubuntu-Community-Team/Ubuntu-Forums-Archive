---
title: "Openvpn Bridging Issues"
date: 2010-11-09
forum: Networking &amp; Wireless
---

### Post by MobiusNZ on 2010-11-09
Hi guys,

I've got an issue trying to get Openvpn up and running in bridged mode.

The remote computer can authenticate and connect and get and IP address and ping the Openvpn server fine.

It can't reach other servers however.

I've run tcpdump on other servers and the vpn server trying to find out the cause of it, and it seems the other servers receive the ARP requests, and send an ARP REPLY, but the vpn server does not see/pass on the ARP REPLY to the remote computer.

Anyone have any ideas?

Here are my config files:

/etc/openvpn/server.conf
```

port 1194
proto udp
dev tap0 
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
tls-server
dh dh1024.pem
ca ca.crt
cert server.crt
key server.key
keepalive 10 60
persist-key
persist-tun
server-bridge 192.168.30.2 255.255.255.0 192.168.30.128 192.168.30.191
push "dhcp-option DOMAIN "mydomain.co.nz"
push "dhcp-option DNS 192.168.30.2"
comp-lzo
status-version 2
status openvpn-status.log
ifconfig-pool-persist pool.log
verb 3
plugin /usr/lib/openvpn/openvpn-auth-pam.so login
username-as-common-name
client-cert-not-required
duplicate-cn
user nobody

```

/etc/openvpn/up.sh:
```

#!/bin/sh

BR=$1
DEV=$2
MTU=$3
/sbin/ifconfig $DEV mtu $MTU promisc up
/usr/sbin/brctl addif $BR $DEV

```

/etc/openvpn/down.sh:
```

#!/bin/sh

BR=$1
DEV=$2

/usr/sbin/brctl delif $BR $DEV
/sbin/ifconfig $DEV down

```

/etc/network/interfaces:
```

# The loopback network interface
auto lo
iface lo inet loopback


auto br0
iface br0 inet static
	address 192.168.30.2
	netmask 255.255.255.0
	gateway 192.168.30.254
	bridge_ports eth0
	bridge_fd 9 
	bridge_hello 2
	bridge_maxage 12
	bridge_stp off

# The primary network interface
iface eth0 inet manual 
	up ifconfig $IFACE 0.0.0.0 up
	up ip link set $IFACE promisc on
	down ip link set $IFACE promisc off
	down ifconfig $IFACE down
```

---

### Post by TSJason on 2010-11-10
Hi,

I imagine that you need to setup the kernel and iptables on the openvpn to act as a router. IE, a POSTROUTING statement in iptables, maybe something like this:

```
iptables -t nat -A POSTROUTING -s 192.168.30.0/255.255.255.0 -j SNAT --to-source 192.168.30.254
```

You should make sure the ip's are right for your environment.

and the net.ipv4.ip_forward sysctl option enabled(set to 1) in /etc/sysctl.conf 

(run "sysctl -p" after enabling to pickup the change in the system)

---

### Post by MobiusNZ on 2010-11-10
Hi Jason,

Hmm - I thought the idea of bridging was that you don't need to route/nat.

If I source-NAT to 192.168.30.254 (the local router), then how would the server pick up the packets and return it to the remote user?

I do have ip forwarding enabled - ARP requests from the remote computer are reaching the local servers, they're just not making it back...

---

### Post by TSJason on 2010-11-10
I don't think I had enough info or I missed something in your previous post. The source nat should be pointing to your openvpn server's host address - not the router.

---

