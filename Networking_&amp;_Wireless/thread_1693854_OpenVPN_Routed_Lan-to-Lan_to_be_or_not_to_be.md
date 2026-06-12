---
title: "OpenVPN Routed Lan-to-Lan: to be or not to be???"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by Debie on 2011-02-23
Ok, I really need help by all of you. :D
This is my situation:

[IMG]http://www.secure-computing.net/wiki/images/thumb/9/90/Ovpn_routing.jpg/800px-Ovpn_routing.jpg[/IMG]

The only differences are:
I have only one OpenVPN Server and one Client;
The IP class are different.
I've configured the OpenVPN Server and Client with the same logic reported here:

[http://www.secure-computing.net/wiki/index.php/OpenVPN/Routing](http://www.secure-computing.net/wiki/index.php/OpenVPN/Routing)

And the configuration files are:

**Server**

[IMG]http://img130.imageshack.us/img130/826/vpns.jpg[/IMG]


**Client**

[IMG]http://img823.imageshack.us/img823/9094/openvpnc.jpg[/IMG]


And these are my routing tables when OpenVPN is running on both side:

**Server**

[IMG]http://img607.imageshack.us/img607/4132/routes.jpg[/IMG]

**Client**

[IMG]http://img535.imageshack.us/img535/3768/routec.jpg[/IMG]


I can reach from LAN A the OpenVPN client on the LAN B.
Same with pc on the LAN B versus OpenVPN server on the LAN A.

**_I can't reach pc on the LAN B from LAN A and viceversa!!_**

What's wrong?
I think routing is correct, firewall is correct (forwading, incoming, output on tun interface is allowed in both openvpn nodes).

Please give me some help, I'm going crazy. :popcorn:


P.S.: I'm testing all inside a network with class ip 192.168.5.x

---

### Post by YesWeCan on 2011-02-23
I gather you have two LANs, A and B, and you would like to use the VPN to allow routing between any PC on LAN A and any PC on LAN B in either direction. Is that right?

Please confirm:
LAN A subnet is 192.168.100.0/24
LAN B subnet is 192.168.2.0/24
the VPN subnet is 192.168.199.0/24
The VPN server is located on LAN A.
You can ping the VPN server from the VPN client and vice-versa.


If this is all correct then you just need to make the VPN server and the VPN client behave like gateway/routers.

Both VPN client and server PCs must have IP forwarding enabled
Each PC on each LAN needs to have its routing table configured so that the local VPN PC is the gateway for IP addresses on the remote LAN.
The iptables on the VPN client and VPN server must allow inputs and forwarding of tun0 traffic

---

### Post by Debie on 2011-02-23
> **YesWeCan said:**
> I gather you have two LANs, A and B, and you would like to use the VPN to allow routing between any PC on LAN A and any PC on LAN B in either direction. Is that right?

Please confirm:
LAN A subnet is 192.168.100.0/24
LAN B subnet is 192.168.2.0/24
the VPN subnet is 192.168.199.0/24
The VPN server is located on LAN A.
You can ping the VPN server from the VPN client and vice-versa.


Confirmed

> 
If this is all correct then you just need to make the VPN server and the VPN client behave like gateway/routers.

Both VPN client and server PCs must have IP forwarding enabled
Each PC on each LAN needs to have its routing table configured so that the local VPN PC is the gateway for IP addresses on the remote LAN.
The iptables on the VPN client and VPN server must allow inputs and forwarding of tun0 traffic

This is just the configuration installed in each network.

[SIZE="1"]Just a question:
I use shorewall firewall and I don't know how to set a FORWARD rule with it.
I had to set it manually: iptables -A FORWARD -i tun+ -j ACCEPT

How can I do this with policy/rules files in shorewall?[/SIZE]

---

### Post by YesWeCan on 2011-02-23
Have you enabled IP forwarding in your kernels?

*from: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)*
```
Enable routing 
[LIST]
[*]Configure the gateway for routing between two interfaces by enabling IP forwarding:
[/LIST]
sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward" 

[LIST]
[*]Edit /etc/sysctl.conf and add these lines:
[/LIST]
net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1
```

I am not familiar with Shorewall. But you have to enable tun+ on both VPN client and server in both the INPUT and FORWARD tables.

---

### Post by Debie on 2011-03-04
Update:
 
The problem was on the ethernet configuration inside Proxmox (the virtual driver was wrong).

---

