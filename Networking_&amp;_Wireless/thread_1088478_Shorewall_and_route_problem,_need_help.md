---
title: "Shorewall and route problem, need help"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by RayVad on 2009-03-06
Got some trouble to get my network routed in the correct way.
Since Shorewall is installed on this machine, i suppose that i should control the access between these local nics.

This is my setup:

   
---eth1(wan)-----| Firewall|----eth0(lan)----

```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# LAN side NIC of POPTOP Server
auto eth0
iface eth0 inet static
        address 192.168.6.10
        netmask 255.255.255.0
        network 192.168.6.0
        broadcast 192.168.6.255
        gateway 192.168.6.1

# WAN side NIC of POPTOP Server
auto eth1
        iface eth1 inet static
        address 10.10.0.10
        netmask 255.255.255.0
        network 10.10.0.0
        broadcast 10.10.0.255
        gateway 10.10.0.254

```
```

> route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.6.0     *               255.255.255.0   U     0      0        0 eth0
10.10.0.0       *               255.255.255.0   U     0      0        0 eth1
default         dsldevice.lan   0.0.0.0         UG    100    0        0 eth1
default         dsldevice.lan   0.0.0.0         UG    100    0        0 eth0

>route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.6.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
10.10.0.0       0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         10.10.0.254     0.0.0.0         UG    100    0        0 eth1
0.0.0.0         192.168.6.1     0.0.0.0         UG    100    0        0 eth0


```

When doing a traceroute it is routing across the wrong NIC:
```

traceroute to www.nu.nl (62.69.184.53), 30 hops max, 40 byte packets
 1  dsldevice.lan (10.10.0.254)  42.205 ms  41.705 ms  41.264 ms
 2  lo1.dr5.d12.xs4all.net (194.109.5.219)  13.035 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  * * *
 7  62.69.184.53 (62.69.184.53)  11.765 ms  11.448 ms  11.623 ms

```

How is this possible? And how can i force (or use shorewall) the correct route for the lan site?

My shorewall configs:
/etc/shorewall/interfaces
```

#ZONE   INTERFACE       BROADCAST       OPTIONS
lan     eth0            192.168.6.255
net     eth1            10.10.0.255
vpn     ppp+

```
/etc/shorewall/policy
```

#SOURCE         DEST            POLICY          LOG             LIMIT:BURST
#                                               LEVEL
fw              net             ACCEPT
fw              lan             ACCEPT
fw              vpn             ACCEPT
lan             fw              ACCEPT
lan             vpn             ACCEPT  debug
vpn             fw              ACCEPT
vpn             net             ACCEPT
net             all             DROP    debug
all             all             REJECT

```
/etc/shorewall/rules
```

#ACTION SOURCE          DEST            PROTO   DEST    SOURCE          ORIG$
#                                               PORT(S) PORT(S)         DEST$
DROP    lan     net     all
ACCEPT  vpn     lan     icmp
ACCEPT  lan     vpn     all
ACCEPT  vpn     vpn     all
ACCEPT  vpn     lan:192.168.6.1 tcp     23,80
ACCEPT  vpn     lan:192.168.6.2 tcp     20,21,445,5900,20000,21000
ACCEPT  vpn     lan:192.168.6.2 udp     20,21,445,5900,20000,21000
REJECT  vpn     lan:192.168.6.3 all
ACCEPT  vpn     lan:192.168.6.4 tcp     5900,20000,21000
ACCEPT  vpn     lan:192.168.6.4 udp     5900,20000,21000
ACCEPT  vpn     lan:192.168.6.10        tcp     22,10000
ACCEPT  vpn     lan:192.168.6.10        udp     22
ACCEPT  vpn     lan:192.168.6.20        tcp     80,5000,5001
ACCEPT  vpn     lan:192.168.6.20        udp     5000
ACCEPT  vpn     lan:192.168.6.70        tcp     22,10000
ACCEPT  vpn     lan:192.168.6.70        udp     22
ACCEPT  vpn     lan:192.168.6.90        tcp     22,80,10000,14534
ACCEPT  vpn     lan:192.168.6.90        udp     22
ACCEPT  vpn     lan:192.168.6.150-192.168.6.159 all
REJECT  vpn     lan:192.168.6.250       all

```

/etc/shorewall/tunnels
```

#TYPE                   ZONE    GATEWAY         GATEWAY
#                                               ZONE
pptpserver              net     0.0.0.0/0

```
/etc/shorewall/zones
```

#ZONE   TYPE            OPTIONS         IN                      OUT
#                                       OPTIONS                 OPTIONS
fw      firewall
net     ipv4
lan     ipv4
vpn     ipv4

```


The routing is via the wrong NIC. And even sometimes over the correct NIC. How do i need to set it up so, that it always routes over 192.168.6.10?

Removing the default gateway for 10.10.0.10, results into losing connection for my pptp server running on eth1 also.
Chancing the default gateway of 10.10.0.10 to 192.168.6.1, also results into failure of the 10.10.0.0 network

Since there is shorewall between, it shouldn't even access the network on eth1, as it should be blocked.

Any ideas or suggestions?

Here is exactly what a mean, 2 traceroutes one another, but making use of different NIC:
```

sudo tracert www.nu.nl
traceroute to www.nu.nl (62.69.184.54), 30 hops max, 40 byte packets
 1  dsldevice.lan **_(192.168.6.1)_**  42.985 ms  42.381 ms  41.862 ms
 2  lo1.dr5.d12.xs4all.net (194.109.5.219)  14.185 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  62.69.184.54 (62.69.184.54)  12.456 ms  10.591 ms  12.439 ms

sudo tracert www.nu.nl
traceroute to www.nu.nl (62.69.184.52), 30 hops max, 40 byte packets
 1  dsldevice.lan **_(10.10.0.254)_**  53.598 ms  53.035 ms  52.563 ms
 2  lo1.dr5.d12.xs4all.net (194.109.5.219)  13.179 ms * *
 3  * * *
 4  * * *
 5  * * *
 6  62.69.184.52 (62.69.184.52)  11.854 ms  10.610 ms  11.636 ms

```

---

