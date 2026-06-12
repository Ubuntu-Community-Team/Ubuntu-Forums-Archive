---
title: "Strange routing behaviour in Ubuntu 10.04.4 LTS"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by helgman on 2012-10-19
OK ...

I have a network with four router, two based on Ubuntu Server 10.4 LTS and two based on Cisco IOS. The four routers are connected in a ring-topology and then LANs are connected to the various routers. Now I've come across a little problem and I'm lost as to how to proceed with the troubleshooting since I can't find a way to make the Ubuntu Server tell exactly what decisions it's making. Here is the problem:

Let's call the Cisco IOS routers A and B, and the Ubuntu Server routers C and D.
The routers are then connected like this: A - B - C - D - A

Most communication in the network works fine, but not all of it. Clients using B as a gateway sometimes finds themselves unable to communicate with clients connected to Ds LANs. Troubleshooting the matter I've come to the following conclusions:

1. Traffic taking the route LAN - B - A - D - LAN reaches its destination
2. Traffic taking the router LAN - B - C - D - LAN gets lost at D
3. Traffic taking the route LAN - C - D - LAN reaches its destination

Using "tcpdump" on D confirms that traffic from the LAN connected to B (or any traffic from the router B going through C) reaches the interface on router D connected to router C. Using "tcpdump" on the LAN facing interface don't show any the captured traffic leaving the router. There is no ICMP traffic sent back to the sender explaining what happens.

If this had been a router running Cisco IOS I would have used various debug commands to try and figure out exactly what happens but I can't find any useful information in Ubuntu and I don't know where to look.

Any suggestions?

(No, there are no iptables on the Ubuntu routers, already checked and re-checked ...)

Regards,
Helgman

---

### Post by conradin on 2012-10-19
traceroute
is a great program for tracing the packets path. 
Im curious about packets taking the path C>B>A>D
This is a bidirectional token ring?
Are you sure theres no iptables? have you looked in the sbin?
Have a look at the route command, and show us the outputs of 
C & D route commands. 

netstat can tell you about what connections youre making, and tcpdump can tell you what packets youre getting from what places. from host D you could run the command: tcpdump host B
and see what, if any traffic makes it to host D.

I would want to know more about whats going on from point B>C

---

### Post by helgman on 2012-10-19
Thanks for your input conradin!

This is not a token-ring but a "ring-topology", that is the devices A-B-C-D are connected in a ring. Sorry for the confusion.

No traffic will traverse the route C - B - A - D unless the link between C and D is taken away.

As I stated in the original post, I know the traffic flow (see points 1-3). I've used tcpdump and I've looked D as the point where traffic "disapears", that is, it can be seen "entering" the router on one interface (the interface pointing towards C) but not exiting on any of the other interfaces.

As I stated in the original post, there are no iptables:
```
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

I've looked through all the routing tables and there is nothing missing in any of them. They are also pointing in the right directions (that is, using the right gateways and interfaces).

The LAN that D should deliver to is directly connected and it delivers if the traffic comes from B via A. If the traffic comes from B via C ... it doesn't. If the traffic comes from C (or a LAN connected to C) it goes through (this is actually an assumption since I'm not physical present ... but a ping from a LAN interface on C to a client on a LAN connected to D works like a charm).

The problem is that I can "see" the traffic entering the router (using tcpdump) but I can't see it exit the router ... no matter what interface I run it on!

Hope this might help clear the picture some.

Regards,
Helgman

---

### Post by helgman on 2012-10-19
UPDATE!

I've been able to dig a bit deeper into the problem. Below is a picture of the network so we all know what we're talking about (sort of): [picture]("http://ubuntuone.com/5oEYo15UViH2sznT0vZRtj")

So the original problem (still a problem) was that communication between network ii and iv didn't work. The packages passed through B (Cisco IOS) and C (Ubuntu Server 12.04.1 LTS), arrived at D (Ubuntu Server 10.04.4 LTS) and then didn't get passed on. If packaged took the other way, that is via B to A (Cisco IOS) and then on through D it all worked just fine.

This afternoon I was able to try the other long and winding path, that between i and iii. And what did I find? The exact same problem!

A package from i passing through A, B and C would arrive at the destination. A package passing through A, D and C would disappear at ... C.

A package going from iii to iv, passing through C and D would arrive at the intended destination. The same thing goes for i to iv, i to ii and ii to iii.

I've temporarily solved the communication problem following the path suggested by conradin - changen the costs so that the link between C and D isn't the preferred route to any destination. But that is not a long-time solution, just a quick fix over the weekend.

One more detail that I missed in my first post: the Ubuntu machines uses BIRD and the routing protocol is OSPF.

Any help would be most appreciated.

Regards,
Helgman

---

### Post by helgman on 2012-10-22
OK ... finally cracked this one!

Turns out it was a problem with asymmetric routing and the way it's handled to prevent spoofing. Changing the rp_filter parameter in sysctl.conf to 0 (or just to try it out under /proc/sys/net/ipv4/conf/[all|default|interface]/) did the trick!

Regards,
Helgman

---

