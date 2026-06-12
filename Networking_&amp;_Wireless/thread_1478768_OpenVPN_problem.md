---
title: "OpenVPN problem"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by Jonnyuser on 2010-05-10
I have a VPN problem.
Behind my VPN client has more subnets. I connected with my VPN server with static key connection without problems. 
Now I need more clients, so static key (based on the documentation) not usable, only certificate based. 
I reconfigure it, connection works perfectly, they can ping each other.
But after this, the subnets behind the client can't reachable. 

Client : 10.0.0.x, 192.168.0.x
Server : Internet, 10.0.0.x

If I see the traffic of the tunnel, I saw the 192.168.0.x packages on the server goes through the tunnel. 
But on the client, they doesn't show up. If I ping the client from the server it goes through the tunnel perfectly.
It seems the 192.168.0.x packages routed to the tunnel well, but the client side drop it before I can see it. Rounting and policies are the same as the static key version. Only OpenVPN settings are different.

Server config :
local x.x.x.x
port 1194
proto udp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem
server 10.0.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
client-config-dir clients
keepalive 10 120
tls-auth ta.key 0 # This file is secret
comp-lzo
persist-key
persist-tun

Client config :

tls-client
dev tun
proto udp
remote x.x.x.x 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
tls-auth ta.key 1
comp-lzo

---

### Post by Jonnyuser on 2010-05-10
Server :
Destination Gateway Genmask Flags Metric Ref Use Iface
10.0.0.2 0.0.0.0 255.255.255.255 UH 0 0 0 tun0
x.x.x.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
192.168.0.0 10.0.0.2 255.255.255.0 UG 0 0 0 tun0
0.0.0.0 x.x.x.1 0.0.0.0 UG 100 0 0 eth0

Client :
10.0.0.1 0.0.0.0 255.255.255.255 UH 0 0 0 tun0
192.168.0.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
0.0.0.0 0.0.0.0 0.0.0.0 U 0 0 0 ppp0

The server's Internet on the eth0, the client's Internet on the ppp0

---

