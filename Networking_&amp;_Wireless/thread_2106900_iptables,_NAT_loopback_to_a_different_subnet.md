---
title: "iptables, NAT loopback to a different subnet"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by erik5678 on 2013-01-20
Hi!

I'm using Toastman Tomato firmware on my router (Linksys E3000) configured with VLAN.

I have divided my network into 3 different subnets, 192.168.0.0/24 (vlan1, br0), 192.168.1.0/24 (vlan3, br1) and 192.168.2.0/24 (vlan4, br2). (WAN is on vlan2). Each of these subnets have their own VLAN. All VLANs are tagged on port 1, which is then connected to a smart switch.

The problem I have now is that my server network (192.168.2.0/24), where my ubuntu server is located, can't be reached from my private or guest networks (the other 2 subnets) using the domain that is linked to my WAN IP. NAT loopback will only loop back to the same subnet. If I open up a port to a web server on the 192.168.0.0/24 subnet, and try to connect to the domain in a browser, it will work. When I instead open up the same port to the server subnet (192.168.2.0/24), NAT loopback will not work anymore.

I have tried to solve this using iptables, but I have not had any success with this. I have tried the following rules:

```

iptables -t mangle -A PREROUTING -i ! WAN -d `nvram get wan_ipaddr` -j MARK --set-mark 0xd001
iptables -t mangle -A PREROUTING -j CONNMARK --save-mark
iptables -t nat -A POSTROUTING -m mark --mark 0xd001 -j MASQUERADE

```

Can anyone help me get this working?

I know that it's bad practice to rely on NAT loopback, but I would like not having two different configurations for SSH, FTP and web clients depending on if I'm at home or not. I also like having the networks completely isolated from each other.

Reaching the server network from the WAN side works just fine.

These are the standard rules that tomato created with NAT loopback set to all, and target set to MASQUERADE.

I think this is the part that needs to be changed, but I don't know what to change it to:
```

   22  8716 SNAT       all  --  *      br0     192.168.0.0/24       192.168.0.0/24      to:192.168.0.1 
    0     0 SNAT       all  --  *      br1     192.168.2.0/24      192.168.2.0/24     to:192.168.2.1 
    0     0 SNAT       all  --  *      br2     192.168.3.0/24      192.168.3.0/24     to:192.168.3.1 

```

I have replaced my WAN IP with [WANIP] before this was posted for security reasons.

Regular rules
```

Chain INPUT (policy DROP 3 packets, 486 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       tcp  --  br2    *       0.0.0.0/0            192.168.3.1        tcp dpt:80 
    0     0 DROP       tcp  --  br1    *       0.0.0.0/0            192.168.3.1        tcp dpt:80 
    0     0 DROP       tcp  --  br2    *       0.0.0.0/0            192.168.2.1        tcp dpt:80 
    0     0 DROP       tcp  --  br1    *       0.0.0.0/0            192.168.2.1        tcp dpt:80 
    0     0 DROP       tcp  --  br2    *       0.0.0.0/0            192.168.0.1         tcp dpt:80 
    0     0 DROP       tcp  --  br1    *       0.0.0.0/0            192.168.0.1         tcp dpt:80 
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
   98  9830 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
   20  3392 ACCEPT     all  --  br0    *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  br1    *       0.0.0.0/0            0.0.0.0/0           
   48  3840 ACCEPT     all  --  br2    *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp spt:67 dpt:68 

Chain FORWARD (policy DROP 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination                          
    0     0 ACCEPT     all  --  br0    br0     0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  br1    br1     0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  br2    br2     0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           state INVALID 
    0     0 TCPMSS     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp flags:0x06/0x02 TCPMSS clamp to PMTU 
 7457  400K restrict   all  --  *      vlan2   0.0.0.0/0            0.0.0.0/0           
31072   46M L7in       all  --  vlan2  *       0.0.0.0/0            0.0.0.0/0           
38529   46M ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
    0     0 DROP       all  --  br0    br1     0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  br0    br2     0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  br1    br0     0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  br1    br2     0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  br2    br0     0.0.0.0/0            0.0.0.0/0           
    0     0 DROP       all  --  br2    br1     0.0.0.0/0            0.0.0.0/0           
    0     0 wanin      all  --  vlan2  *       0.0.0.0/0            0.0.0.0/0           
    0     0 wanout     all  --  *      vlan2   0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  br0    *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  br1    *       0.0.0.0/0            0.0.0.0/0           
    0     0 ACCEPT     all  --  br2    *       0.0.0.0/0            0.0.0.0/0           
    0     0 upnp       all  --  vlan2  *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 141 packets, 28731 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain restrict (1 references)
 pkts bytes target     prot opt in     out     source               destination         
 7453  399K rres00     all  --  *      *       0.0.0.0/0            0.0.0.0/0           
 7446  399K rres01     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain upnp (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain wanin (1 references)
 pkts bytes target     prot opt in     out     source               destination         

Chain wanout (1 references)
 pkts bytes target     prot opt in     out     source               destination         


```

NAT rules:
```

Chain PREROUTING (policy ACCEPT 462 packets, 45802 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DROP       all  --  vlan2  *       0.0.0.0/0            192.168.0.0/24      
    0     0 DROP       all  --  vlan2  *       0.0.0.0/0            192.168.2.0/24     
    0     0 DROP       all  --  vlan2  *       0.0.0.0/0            192.168.3.0/24     
    5   377 WANPREROUTING  all  --  *      *       0.0.0.0/0            [WANIP]       
    5   377 upnp       all  --  *      *       0.0.0.0/0            [WANIP]       

Chain POSTROUTING (policy ACCEPT 8 packets, 2113 bytes)
 pkts bytes target     prot opt in     out     source               destination         
   82  5679 MASQUERADE  all  --  *      vlan2   0.0.0.0/0            0.0.0.0/0           
   22  8716 SNAT       all  --  *      br0     192.168.0.0/24       192.168.0.0/24      to:192.168.0.1 
    0     0 SNAT       all  --  *      br1     192.168.2.0/24      192.168.2.0/24     to:192.168.2.1 
    0     0 SNAT       all  --  *      br2     192.168.3.0/24      192.168.3.0/24     to:192.168.3.1 

Chain OUTPUT (policy ACCEPT 48 packets, 9798 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain WANPREROUTING (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           to:192.168.0.1 

Chain upnp (1 references)
 pkts bytes target     prot opt in     out     source               destination         
    4   337 DNAT       udp  --  *      *       0.0.0.0/0            0.0.0.0/0           udp dpt:24015 to:192.168.0.24:24015 
    0     0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0           tcp dpt:24015 to:192.168.0.24:24015 

```

Help would be very much appreciated.

/Erik

---

### Post by iponeverything on 2013-01-20
I'd flush everything and then just configure bare minimum required for your basic architecture (VLAN's) Get it working -- then start adding the extra layers of NATs and filters. Debug each layer before moving on to the next.

What you have now is an exercise in unnecessary complexity, but that's all part of the fun..

---

### Post by erik5678 on 2013-01-20
> **iponeverything said:**
> I'd flush everything and then just configure bare minimum required for your basic architecture (VLAN's) Get it working -- then start adding the extra layers of NATs and filters. Debug each layer before moving on to the next.

What you have now is an exercise in unnecessary complexity, but that's all part of the fun..

The problem is that the rules that are already in place are generated by the router firmware, and can only be temporary flushed. As soon as the router or the firewall service restarts, these rules are added back in again. The only thing I can really change is that I can remove all the NAT loopback rules, and add new rules to a firewall script.

Thank you for your suggestion though.

/Erik

---

