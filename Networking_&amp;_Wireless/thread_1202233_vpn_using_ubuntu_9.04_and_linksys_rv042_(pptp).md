---
title: "vpn using ubuntu 9.04 and linksys rv042 (pptp)"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by sebas-aguirre on 2009-07-02
Hi.
I have a linksys rv042 acting as a vpn server.
I have connected to it from a remote location using windows xp. Everything works great.
Now I am trying to connect to it from ubuntu 9.04
I have created the vpn connection.
I am able to connect to the vpn.
Problem is every request I make does not seem to realize I have a vpn set.
For example, I go to a local site in the vpn network (192.168.2.34) and it tries to go through the internet connection I have, not realizing I have a vpn.
I did a traceroute to 192.168.2.34 and it never gets even to the public address of the router where the vpn is.
I think I must be missing some configuration but it's hard to find the exact data I need.
The data of the vpn on ifconfig is this:

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.2.200  P-t-P:192.168.2.200  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:120 (120.0 B)  TX bytes:132 (132.0 B)

I've been reading the forum and I read a post where someone suggests adding a line like this after connecting to the vpn.

sudo route add -net 192.168.2.0 netmask 255.255.255.0 dev ppp0

I have done that but it donesn't work.
What I find strange is that "ip route show" says 192.168.2.0/24 while my address is 200
Please any help appreciated.

---

