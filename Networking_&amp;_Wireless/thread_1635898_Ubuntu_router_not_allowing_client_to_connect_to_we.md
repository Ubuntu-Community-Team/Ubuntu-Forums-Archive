---
title: "Ubuntu router not allowing client to connect to web"
date: 2010-12-02
forum: Networking &amp; Wireless
---

### Post by tanusfarms on 2010-12-02
I recently built a ubuntu router useing a old pc. it runs with ubuntu 10.04 server and has 3 ports. 1 wan (eth0) and 2 lan (eth1 and eth2). no wireless on it at all. i connect to the web through a linksys router. so my network consists off (in order of connections) my cable modem, my linksys router, my ubuntu router, clients. I connect this way because my linksys has other clients plugged into it. 

From my ubuntu router i have internet access and can ping the client attactched to it. from that client I can ping all the ports in the router. However there is no internet access on my client. 

I know my Ipv4 forwarding is turned on and I don't have anything listed in the iptables that is restricting the network. 

Destination |        Gateway                | Genmask                  | Flags     | Iface
192.168.1.0        | 0.0.0.0                  | 255.255.255.0        | U              | eth0
192.168.15.0 |      0.0.0.0                 | 255.255.255.0         | U        | eth2
192.168.10.0     | 0.0.0.0                  | 255.255.255.0         | U               | eth1
0.0.0.0                  | 192.168.1.1 |         0.0.0.0                        | UG            | eth0

Is what is showing for my current routing table. I am new to ubuntu and 
fairly new to networking so If I am overlooking something please 
let me know.

currently it is easiest for me to connect online and look up info via the client by just plugging 
it into the linksys router so posting what i get via command responses isn't always that easy so bare with me. 

thanks in advance for any help you might provide it is apprechiated.

---

