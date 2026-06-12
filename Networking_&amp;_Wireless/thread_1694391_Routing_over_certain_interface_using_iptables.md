---
title: "Routing over certain interface using iptables"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by tincup on 2011-02-24
Hi.

I am establishing a VPN connection with a Cisco VPN server, but only want outgoing connections to a certain set of IP addresses to actually go through the VPN. I tried something like this:

```
sudo iptables -A OUTPUT -t mangle -p tcp -d 111.222.0.0/16 -j ROUTE --oif tun0

```

but keep getting ```
iptables v1.4.4: unknown option `--oif'
```

Any ideas? Is it the correct approach anyway?

I am on Ubuntu 10.04.

Best,
 Jan

---

### Post by SeijiSensei on 2011-02-24
Use the routing commands, not iptables.

First, set up the VPN connection. Then run the command:

```
ip route add 192.168.1.0/24 via tun0
```

replacing 192.168.1.0/24 with the network address and subnet mask of the IPs you wish to reach over the tunnel.

---

### Post by tincup on 2011-02-25
Thanks for pointing out ip route. So I tried playing around with it a little, but without success. My original setup (I connect over wlan in a 192.168.178.x network to a local access point) is like this:

```
192.168.178.0/24 dev wlan0  proto kernel  scope link  src 192.168.178.29  metric 2 
169.254.0.0/16 dev wlan0  scope link  metric 1000 
default via 192.168.178.1 dev wlan0  proto static 
```

After connecting to the vpn via vpnc, it looks like this (real IPs are masked):

```
A.B.213.226 via 192.168.178.1 dev wlan0  src 192.168.178.29  mtu 1500 advmss 1460
192.168.178.0/24 dev wlan0  proto kernel  scope link  src 192.168.178.29  metric 2
A.B.19.0/24 dev tun0  scope link
169.254.0.0/16 dev wlan0  scope link  metric 1000
default dev tun0  scope link
```

The actual correct routing already seems to be in there with 
```
A.B.19.0/24 dev tun0  scope link
```. 

So I tried removing the default route through tun0 (last line) and adding again ```
default via 192.168.178.1 dev wlan0  proto static 
```

Without success, cannot connect to anything. 

Any ideas?

Best, 
 tin

---

### Post by SeijiSensei on 2011-02-25
The other end of the VPN has to have routing properly configured as well, so it knows where to send packets destined for your VPN address.  Do you know if it's set up correctly at both ends?  

Let's suppose you had a VPN that gave you 10.1.1.1 as your VPN address with a point-to-point connection to 10.1.1.2.   If that machine's not the default gateway for the remote A.B.19.0/24 network, machines in that address block will send traffic for your 10.1.1.1 address to their default gateway, which may have no idea what to do with it.  Routing is tricky and requires correct configurations at both ends.

---

### Post by tincup on 2011-02-28
Thanks for your response! I played around a little. Using the "target networks" directive in the vpnc config file did exacly what I wanted. Still, the VPN server should automatically push these information to the client, so I will connect the IT guys.

Best, Tin

---

