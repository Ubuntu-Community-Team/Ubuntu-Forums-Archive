---
title: "routing problem"
date: 2012-12-21
forum: Networking &amp; Wireless
---

### Post by KisteBecks on 2012-12-21
Hi fellow users :)

got this network setup:

inet - router1(172.16.0.1) - (172.16.0.2)router2(192.168.11.171) - switch - openvpn server(192.168.11.85)

on router1 i added this route:
```

route add -net 192.168.11.0 netmask 255.255.255.0 gw 172.16.0.1 dev br-lan

```now i can ping the openvpn server from router1, but still i cant reach the openvpn server over the internet.

this is the port forwarding rule on router1:
```

 iptables -t nat -I PREROUTING -p udp --dport 3000 -j DNAT --to-destination 192.168.11.85:1194

```

what else do i need to be able to connect to the openvpn server inside my home lan?

---

### Post by Doug S on 2012-12-21
Shouldn't your route be:```
route add -net 192.168.11.0 netmask 255.255.255.0 gw 172.16.0.[COLOR=#ff0000]2[/COLOR] dev br-lan
```And if things still do not work, maybe you need two port forwardings, one in each router.
Router 1:```
iptables -t nat -I PREROUTING -p udp --dport 3000 -j DNAT --to-destination 172.16.0.2:3000
```Router 2:```
iptables -t nat -I PREROUTING -p udp --dport 3000 -j DNAT --to-destination 192.168.11.85:1194
```

---

### Post by KisteBecks on 2012-12-21
EDIT: sry doug didnt see your post, didnt refresh the page
doug: ah yes the route was wrong....crap. will test that tomorrow. but your iptables commands look right :)


its actually pretty easy, get rid of the route command and do port forwards.

one from router1 to router2:
```

external interface:3000 to 127.16.0.2:3000

```(no code since the openvpn webinterface works so nice)

and one from router2 to openvpn server:
```

iptables -t nat -A PREROUTING -i eth1 -p udp --dport 3000 -j DNAT --to-destination 192.168.11.85:1194

```that was for ingoing packages and the outgoing part is handled by NAT, each router does its own NAT.

---

