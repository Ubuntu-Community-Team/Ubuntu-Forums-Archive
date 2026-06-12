---
title: "IPSEC connection with OpenSwan"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by shemhamforash on 2011-04-11
Hey guys!

Have been trying for weeks now and still can't seem to find the right solution for my problem. What I'm trying to accomplish is the following:

- Computer with 2 ethernetports running OpenSwan:
* WAN (eth0): A.A.A.A
* LAN (eth1): 10.119.129.1/24

- Cisco VPN Concentrator 3000:
* WAN: B.B.B.B
* LAN: 10.119.70.0/24

So the setup looks like this:

10.119.129.1/24 - [Computer] - A.A.A.A - [INTERNET] - B.B.B.B - [VPN concentrator] - 10.119.70.0/24

My configuration is as follows:

Contents of /etc/ipsec.conf

```
version 2.0
config setup
        plutodebug=all
        protostack=netkey
        oe=off
        nhelpers=0

include /etc/ipsec.d/*.conf
```

Contents of /etc/ipsec.d/eevpn.conf

```
conn eevpn
        type=tunnel
        # Networks
        left=A.A.A.A
        right=B.B.B.B
        leftsubnet=10.119.129.0/24
        rightsubnet=10.119.70.0/24
        leftnexthop=%defaultroute
        auto=start
        rekey=yes
        aggrmode=yes
        # Phase 1
        auth=esp
        authby=secret
        keylife=28800s
        ike=3des-md5-modp1024
        pfs=no
        # Phase 2
        esp=aes256-md5
```

Contents of /etc/ipsec.d/eevpn.secrets

```
A.A.A.A B.B.B.B : PSK "secretpassword"
```

And the output of "iptables -L":

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     esp  --  anywhere             anywhere            
ACCEPT     ah   --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:isakmp dpt:isakmp 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     esp  --  anywhere             anywhere            
ACCEPT     ah   --  anywhere             anywhere            
ACCEPT     udp  --  anywhere             anywhere            udp spt:isakmp dpt:isakmp
```

When I start the IPSEC connection the tunnel is established successfully, verified by "ipsec setup --verify":

```
IPsec running  - pluto pid: 30588
pluto pid 30588
1 tunnels up
some eroutes exist
```

However, packets never arrive at the other end. No routes are added to the routing table by OpenSwan.

Output of "route" on the computer:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
A.A.A.A         *               255.255.255.0   U     1      0        0 eth0
10.119.129.0    *               255.255.255.0   U     1      0        0 eth1
default         internet        0.0.0.0         UG    0      0        0 eth0
```

When I ping an IP at the other end of the tunnel (from the computer to the VPN concentrator), I get a destination unreachable message. IP forwarding is on.

Anyone have any clue as to why this is happening? Pointers in the right direction? Do I need to add some more iptable rules? I have no clue anymore :(

Thanks in advance!

---

