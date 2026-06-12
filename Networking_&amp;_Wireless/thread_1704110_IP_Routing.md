---
title: "IP Routing"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by johnc2k on 2011-03-10
Hi Guys,

I have a private lan (not connected to the internet) for software testing. My lan consists of a XP Client, and a Ubuntu Box running Inetsim. (Static IPs, no DHCP).

```
XP Client:
IP: 192.168.100.10
Mask: 255.255.255.0
GW: 192.168.100.1
DNS: 192.168.100.1
```

```
Ubuntu Box:
IP: 192.168.100.1
Mask: 255.255.255.0
GW: 192.168.100.1
DNS: 192.168.100.1
```

I need to be able to route all public IP addresses back to my Ubuntu box, currently I only know how todo this on a per port basis: :(

Here is what I currently do:

```

echo "1" > /proc/sys/net/ipv4/ip_forward

iptables -t nat -A PREROUTING -s 213.x.x.x -p tcp --dport 80 -j DNAT --to-destination 192.168.100.1:80

```
(213.x.x.x being a public IP I detect at time of testing).

Ive tried a few different iptable rules but with no luck,

Any help would be great

Thanks

---

