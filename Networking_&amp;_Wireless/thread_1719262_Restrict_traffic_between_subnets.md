---
title: "Restrict traffic between subnets?"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by darrenshaffer1 on 2011-04-01
I have 3 subnets and an internet connection connected to the server(=4 nics).  I'm looking to block traffic from one subnet to another but allow internet access.  The other 2 are able to communicate with each other and have internet access.

With my configuration all subnets have internet access and access to all subnets.

Here is the configuration files...

interfaces
```

auto eth0
#
iface eth0 inet static
        address 10.0.8.1
        netmask 255.255.255.0
        broadcast 10.0.8.255
        post-up iptables-restore < /etc/iptables.up.rules

#
auto eth1
iface eth1 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        gateway 192.168.0.1

#
auto eth2
iface eth2 inet static
        post-up route add -net 192.168.6.0 netmask 255.255.255.0 gw 192.168.6.1 eth2
        address 192.168.6.1
        netmask 255.255.255.0
        broadcast 192.168.6.255


auto eth3
iface eth3 inet static
        post-up route add -net 192.168.5.0 netmask 255.255.255.0 gw 192.168.5.1 eth3
        address 192.168.5.1
        netmask 255.255.255.0
        broadcast 192.168.6.255


```

route print out
```

10.0.8.0        ubuntu          255.255.255.248 UG    0      0        0 eth0
192.168.6.0     ubuntu          255.255.255.0   UG    0      0        0 eth2
192.168.6.0     *               255.255.255.0   U     0      0        0 eth2
192.168.5.0     ubuntu          255.255.255.0   UG    0      0        0 eth3
192.168.5.0     *               255.255.255.0   U     0      0        0 eth3
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth1

```

iptables rules
```

-P INPUT DROP
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-A INPUT -m state --state ESTABLISHED -j ACCEPT
-A INPUT -m state --state RELATED -j ACCEPT
-A INPUT -i eth2 -j ACCEPT
-A INPUT -i eth3 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 9001:9005 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 41700:41797 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 3389 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 82 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 8081 -j ACCEPT
-A INPUT -p tcp -m tcp --dport 4100 -j ACCEPT
-A INPUT -i eth1 -p icmp -j ACCEPT
-A FORWARD -o eth2 -j ACCEPT
-A FORWARD -o eth3 -j ACCEPT

```

Since all 3 subnets are directly connected to the server for segregation, I believe there is a solution by creating an iptables rule but I don't know how it's done.  I've tried setting rules, in iptables, to deny traffic to and from eth0 but nothing works.  What I'm trying to accomplish is restricting traffic from 10.0.8.0 to any other subnet except for the internet.  Maybe I'm doing it wrong?  Can someone help me? Please?

---

### Post by darrenshaffer1 on 2011-04-04
Bump....  Anyone?

---

### Post by alphacrucis2 on 2011-04-04
> **darrenshaffer1 said:**
> Bump....  Anyone?

You could add a rule for each pair of matching subnets that you don't want to talk to each other and add either -j DROP or -j REJECT as suits your fancy. If you use -j DROP then the connection attempts will just timeout from the user point of view. Whereas -j REJECT will kill the connection attempt immediately. You need to add to the beginning of your FORWARD chain the following (these allow established/related connections through without further checking (compare to what you already have in the INPUT chain.

-A FORWARD -m state --state ESTABLISHED -j ACCEPT
-A FORWARD -m state --state RELATED -j ACCEPT

then add whatever DROP/REJECT rules you want. For example drop any traffic flowing either way between eth2 & eth3

-A FORWARD -i eth2 -o eth3 -j DROP
-A FORWARD -i eth3 -o eth2 -j DROP

or you could check actual source/dest ip's:

-A FORWARD -s 192.168.5.0/24 -d 192.168.10.0/24 -j DROP
-A FORWARD -s 192.168.10.0/24 -d 192.168.5.0/24 -j DROP

Actually I don't think you had a 192.168.10.0/24 subnet but hopefully you get the idea.

I notice that your FORWARD chain has a default policy of ACCEPT. An alternative is to change it to a default policy of DROP or REJECT then add rules for the things that you want to allow. That way anything you don't explicitly allow will be blocked. Check out the various iptables howto's on the net.

Just in case you are not sure about INPUT, OUTPUT and FORWARD.

The INPUT chain only inspects packets that are deemed to be destined to the device itself after the routing descision is made.

The OUTPUT chain only inspects packets that are sourced from the device itself.

All traffic deemed to be transitting (ie in one external interface and out another) are processed by the FORWARD chain.

---

### Post by darrenshaffer1 on 2011-04-05
I tried using just the interface input and output but that didn't work.  I was still getting pings through to other subnet.  I tried the specific destination and source but that didn't work until I put it in the proper order.  It's really picky like that.

Thanks for the help!  Much appreciated!:D

---

