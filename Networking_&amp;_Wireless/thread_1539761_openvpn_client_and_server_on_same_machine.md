---
title: "openvpn client and server on same machine"
date: 2010-07-26
forum: Networking &amp; Wireless
---

### Post by SergeiFranco on 2010-07-26
Hi,

Trying to figure out how to run openvpn client as server.
Here is the reason why I want to do it:

Imagine two cities thousands kilometres apart.
There are two VPN servers one in each city.
There are clients that connect to those VPN servers.
I need a way to connect two VPN servers with VPN tunnel.
E.G.:
(client 1..10)<-->vpn1<--- 1000km ---->vpn2<-->(client 11--20)

Currently I have the following setup (simplified version):


(client 1..10)<-->vpn1<--- 1000km ---->(client 11--20)

There is a problem with latency and pipe throughput if for example client 11 wants to access client 12.

The clients have their IP addresses assigned by VPN server (via config file, each client has permanent IP). In this example neither of clients can access each other without VPN.

I want the ability of client connecting to either vpn1 or vpn2 depending if they move cities.

What I can't figure out is how to deploy so that vpn1 and vpn2 have a tunnel that is bridged with their tunX devices.

My ideas is running TAP-TUN bridge in each server where each TAP is endpoint for tunnel between the vpn servers...

---

