---
title: "Needing to route packets between Ethernet bridge."
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-05-24
So what I want to do is I want the incoming packets to go to br1 of eth2, but I need the outgoing packets to go to eth1 or br0, it really doesn't matter to me really. So basically here's my setup as of now:
```

br0
br1
eth1
eth2
```
So I've enabled IP forwarding, but it still doesn't appear to be working. So since I've enabled IP forwarding the routes changes to:
```
192.168.1.1
```
To the following:
```
192.168.2.1
```
Then for some odd reason I didn't have a Gateway set, so I added my default Gateway by running:
```
route add default gw 192.168.1.254
```
Since I wanted br1 to reach the Internet instead of br1, I made the default route as eth1 by running the following:
```
iptables -t nat -j POSTROUTING -o br0 -s MASQUERADE
```
I've also made sure the network is added, but it still seems that br1 is not reaching the Internet, it's pretty strange and I'm not sure why br1 is not reaching the net. I ran the following to make sure if it just wasn't me:
```
route add -net 192.168.1.1 netmask 255.255.255.0 eth1
```
Then rechecked my kernel routing table and everything appeared to be OK, but it is still not working and as stated before br1 is not able to reach the net. So now I'm thinking the IP forwarding step didn't work, so to make sure I ran the following command:
```
echo 1 > /proc/sys/net/ipv4/ip_forward
```
So IP forwarding is there, but br1 is still acting up. So I'm not really sure what I should do now, I mean I think I've done everything correct, but it's obvious I didn't because it's not working. ;-).

---

