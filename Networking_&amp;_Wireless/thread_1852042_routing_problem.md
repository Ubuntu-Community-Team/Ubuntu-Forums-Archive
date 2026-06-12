---
title: "routing problem"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by deadtom on 2011-09-29
Kubuntu 10.10

I'm connecting to my openvpn server at home just fine but it appears that a route isn't getting created. I don't want ALL of my traffic routed through the VPN, only requests to the 192.168.57.0 network.

My VPN client is given the IP 192.168.57.9, the server is 192.168.57.1.

Here is my route table immediately after the VPN connection is made:
```

10.0.2.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.57.0    0.0.0.0         255.255.255.0   U     0      0        0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.2.2        0.0.0.0         UG    0      0        0 eth0

```If I try to ping the server at 192.168.57.1, I get a Destination Host Unreachable.

So to make the route I do this:

```
sudo route add -net 192.168.57.0 netmask 255.255.255.0 gw 192.168.57.1 dev tap0
```And I end up with this routing table:

```
10.0.2.0        0.0.0.0         255.255.255.0   U     1      0        0 eth0
192.168.57.0    192.168.57.1    255.255.255.0   UG    0      0        0 tap0
192.168.57.0    0.0.0.0         255.255.255.0   U     0      0        0 tap0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.0.2.2        0.0.0.0         UG    0      0        0 eth0

```I STILL can't ping 192.168.57.1.

I can't figure out what I'm doing wrong.

Thanks!

---

### Post by SeijiSensei on 2011-09-29
Are you sure that pings (ICMP) aren't being blocked by a firewalling rule somehow?  If I set up an OpenVPN connection, I can ping either end from the other as soon as the connection is established.

How is routing configured on the other server?  Does it have a route for 192.168.57.0/24 on its end that uses the tunnel?  Sometimes failed pings indicate a routing problem at the other end of the connection.

I'm guessing the server connects to other machines in 192.168.57.0/24 directly.  Don't put the tunnel IPs in the same network space as the rest of the network.  Give them an entirely separate pair of addresses like 10.1.1.1 and 10.1.1.2.  I bet your problem will go away if you do that.

---

### Post by deadtom on 2011-09-29
I can ping 192.168.57.1 from my windows box, over the VPN, just fine so I know ICMP isn't being blocked.

The rest of the network is a 192.168.58.x network so that isn't an issue either.

---

### Post by collisionystm on 2011-09-29
You need to remove this
192.168.57.0    0.0.0.0         255.255.255.0   U     0      0        0 tap0

---

### Post by collisionystm on 2011-09-29
What does your firewall config look like?

iptables-save > /firewall.config

cat firewall.config

paste contents. Hide your public IP please.

---

### Post by deadtom on 2011-09-29
> **collisionystm said:**
> You need to remove this
192.168.57.0    0.0.0.0         255.255.255.0   U     0      0        0 tap0


Tried that, no good. :(

---

### Post by deadtom on 2011-09-29
Whoa, figured it out. Was totally looking in the wrong direction.

I was looking at the client log and noticed errors about compression, specifically that comp-lzo was specified on the client side and not on the server.

So I opened my client.ovpn, hashed out the comp-lzo entry and reconnected.

Viola! Pinging fine. No route entries necessary.

Working beautifully now.

Thanks for the responses though. Very much appreciated.

---

