---
title: "confused about IP Numbering"
date: 2009-05-12
forum: Networking &amp; Wireless
---

### Post by robson9776 on 2009-05-12
Dear all,

I'm very newbie in networking area, so better for me to describe my situation first...

I have a laptop with 2 network interface (LAN and Wireless) and I also have a Linksys wireless router WRTP54G.

now, here's what I want to do...

I want to connect my laptop to a wireless network (IP is automatically given), then I want to share this connection using Linksys by connecting it to my LAN on laptop.

in result, all of my clients can connect to the internet through Linksys.

here's some illustration to make it clear :

**local LAN (192.168.15.xx)** <--> **(eth0 192.168.15.1) Linksys (eth1 192.168.88.1)** <--> **(eth0 192.168.88.2) My Laptop (wlan0 auto/DHCP)** <--> **internet**

what I'm confusing about is gateway IP number on each segment. for example what is default gateway should I use on my laptop, clients and how's the routing table on those 2 routers...?

please kindly help me on this... :confused:

---

### Post by puppywhacker on 2009-05-12
so you are not confused about ip-addresses, your confused about routing.

each node know how to route to "the next hop" because the ip-addresses are in the same subnet. so routing between x.y.z.1 and x.y.z.2 work automatically. what doesn't work is the ones that do not fit the netmask (same as subnet) so you can use the default gateway to reach the not so near networks. so each node will have to have the next hop as a default gateway until you reach the internet. on the return path you have to specify the routes on how to reach your 15 network from the 88 network. 

After you set up all the routing tables so that all networks can be found and all default gateways point to the next node that will lead to the internet; After that you will have to setup a NAT since 192.168 address are not routable from the internet.

NAT setup is done something like this (from the top of my head, so use 'the google')
iptables A XXXXX -j masq
iptables-save
syscfg -w sys.net.ipv4.forwarding=1

---

### Post by robson9776 on 2009-05-12
Yes, you're right. I guest I have a problem with routing, not IP address.

OK, so is this the correct setting :

Local LAN :
IP : 192.168.15.xx
Sub : 255.255.255.0
Gateway : 192.168.15.1

Linksys Eth0 :
IP : 192.168.15.1
Sub : 255.255.255.0
Gateway : leave it blank?

Linksys Eth1 :
IP : 192.168.88.1
Sub : 255.255.255.0
Gateway : leave it blank?

Laptop Eth0 :
IP : 192.168.88.2
sub : 255.255.255.0
Gateway : leave it blank?

Laptop Wlan0 :
IP : automatic
Sub : automatic
Gateway : automatic

as long as my Linksys and laptop can do IP forwarding, then there will be no problem, right?

---

### Post by puppywhacker on 2009-05-13
your list is almost correct, the gateway on the linksys router should point to 192.168.88.2. The reason is that otherwise it will be abled to route the traffic within your 2 networks, but not any traffic directed out over your laptop.

The other thing is that your laptop doesn't know about the 192.168.15.X network so you need to add a route there like so
```
ip route add 192.168.15.0/24 via 192.168.88.1
```

You're also correct that you need to have ip-forwarding enabled. It is disabled by default so you won't unknowningly be a gateway.

if you have set up the routes you should be abled to PING the ip addresses, test it between the links in the network, and throughout your networks.

The only thing is that you still need to masquerade the fact that you are using martian addresses, the 192.168.x.y range is reserved for private use, so to connect them to the real internet you need to translate them to the real address. In your case that means that your laptop has to masq all the incoming traffic over eth0 that is outgoing over wlan0 has to NAT that traffic.

```
sudo iptables -A POSTROUTING -t nat -i eth0 -o wlan0 -j MASQUERADE
sudo iptables-save
```

goodluck

---

