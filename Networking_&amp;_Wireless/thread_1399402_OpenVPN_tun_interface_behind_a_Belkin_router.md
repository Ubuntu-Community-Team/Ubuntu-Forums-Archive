---
title: "OpenVPN tun interface behind a Belkin router"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by Will Shackleton on 2010-02-05
Hi, I have quite an odd problem setting up an OpenVPN server (tun interface) on a computer, behind a Belkin router with a NAT firewall.

I can connect to the VPN from an external internet connection (through my phone as a mobile broadband dongle), and have set up port forwarding on the router. From there I can access services on the VPN server.

The reason that I am using a tun interface rather than a tap interface is that I want the clients to be able to connect to my home network, and only to be able to access one or two PCs on the network. At the moment I am just trying with all PCs (see VPN conf)

However, even though I have enabled ip_forwarding and messed around with a few ip masquerading settings, I can't access any other PCs.

My network IP address is 10.4.1.0, and I am trying to set up the VPN clients to be on 10.4.2.0
I actually have two Belkin routers, but one is just a bridge, due to the physical layout of my network. The server, running on an unused laptop, has to go through both these routers (the bridging router doesn't affect anything else on my network).
The main DSL router is 10.4.1.1, the secondary router is 10.4.1.2, and the server is 10.4.1.9.
The main router is a Belkin F5D9630-4, and the bridge is a F5D9230-4.

Fortunately, both the routers have ssh access, and I can access the route command. Since the OpenVPN tun didn't work at first, I tried adding a route to the router so that the routing table looked like this on the main router:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
pub.ip.1.4      *               255.255.255.255 UH    0      0        0 ppp_0_0_38_1
10.4.1.0        *               255.255.255.0   U     0      0        0 br0
10.4.2.0        10.4.1.9        255.255.255.0   UG    1      0        0 br0
default         pub.ip.1.4      0.0.0.0         UG    0      0        0 ppp_0_0_38_1
```However this still didn't work.

(Note):
The proprietary route command uses: (this is the custom version on the router, and the router does also have BusyBox, which has another version of this command)
```
Usage: route add <IP address> <subnet mask> <[ from <gateway>] [<interface>]>
```and I tried:
```
route add 10.4.2.0 255.255.255.0 10.4.1.9 br0
```My OpenVPN config is:
```
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
dh dh1024.pem
server 10.4.2.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 10.4.1.0 255.255.255.0"
push "redirect-gateway"
keepalive 10 120
comp-lzo
max-clients 10
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
client-cert-not-required
username-as-common-name
plugin /usr/lib/openvpn/openvpn-auth-pam.so login
```I did also look in to dd-wrt, but it isn't supported for my router. However, I think it has the same chipset, so I may try that.

Any help with OpenVPN config, network routing, or dd-wrt would be greatly appreciated.
Thanks,
Will Shackleton

---

### Post by Will Shackleton on 2010-02-06
I think I have managed to solve this problem now; I disabled compression and added some more route rules to both routers, and all seems to be working now. I also changed some ip masquerading settings.
:KS

---

