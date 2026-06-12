---
title: "Load Balance or Aggregate(combine) Internet Connections"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by megamanexent on 2010-05-12
Hello, 
         This is my first thread I have created here, I have been very good with Google.

My problem is that I would like to load balance or aggregate 2 separate Internet connections on my laptop. Currently a hard line ISP is not available so I'm using an Sierra Wireless 885 USB air card.  Thing is the card is quite slow. I also can tether an iPhone to the laptop. The ideal solution would be to have both connections being utilized to help speed up the overall experience, even if it is only a modest gain in speed. 

I have found articles that can help, but as I do not know much about iptables and basic TCP/IP routing, I'm finding it difficult to implement those solutions. If someone can point me in the right direction ( a slightly dumb down how:to? or better explained? ) or explain how to go about this, I would appreciate it. 

BTW, both phone and aircard get dynamic IP's. Running Ubuntu 10.4

---

### Post by megamanexent on 2010-05-19
No one can point me in the right direction? :(

---

### Post by anthonyj460 on 2010-08-19
it may be a little late for you. and i havent actually tried this myself. i mearly have been curious as to how its done and this is what i keep finding. so here is a script that i got from [[COLOR="red"]here[/COLOR]]("http://www.go2linux.org/load-balance-traffic-for-two-isps-with-linux"). and this is a good place for most routing stuff [[COLOR="Red"]here[/COLOR]]("http://lartc.org/lartc.html")

```
#!/bin/bash -v
#just to be clear IF1 corresponds to P1, P1_NET, and IP1
# IF2 corresponds to P2, P2_NET, and IP2


#IPs of your device connected to the internet

IP1=190.84.224.246
IP2=190.156.148.160

# For Dynamic Connections (change 190.84. to match the beginning of your ip connected to the intenet)
#IP1=`ifconfig | awk -F: '/190.84./ {print $2}' | awk '{ORS=" "; print $1}' | awk '{print $1}'`
#IP2=`ifconfig | awk -F: '/190.156./ {print $2}' | awk '{ORS=" "; print $1}' | awk '{print $2}'`

#Your Gateways (type route in terminal it should be in the same line as default)

P1=190.84.224.1
P2=190.156.148.1

#Your Subnets
P0_NET=192.168.0.0/16 # your local network subnet, but i dont think you are sharing...
P1_NET=190.84.224.0/24 # Part of your gateway, P1 but replacing the 1 at the end with 0/24
P2_NET=190.156.148.0/23# Part of your gateway, P2 but replacing the 1 at the end with 0/23

# NICs your internet interfaces

IF1=eth0
IF2=eth1

ip route add $P1_NET dev $IF1 src $IP1 table T1
ip route add default via $P1 table T1
ip route add $P2_NET dev $IF2 src $IP2 table T2
ip route add default via $P2 table T2

ip route add $P1_NET dev $IF1 src $IP1
ip route add $P2_NET dev $IF2 src $IP2

#ip route add default via $P1

ip rule add from $IP1 table T1
ip rule add from $IP2 table T2

ip route add $P0_NET dev $IF0 table T1
ip route add $P2_NET dev $IF2 table T1
ip route add 127.0.0.0/8 dev lo table T1
ip route add $P0_NET dev $IF0 table T2
ip route add $P1_NET dev $IF1 table T2
ip route add 127.0.0.0/8 dev lo table T2

route del -net 0.0.0.0 netmask 0.0.0.0 dev $IF1
ip route add default scope global nexthop via $P1 dev $IF1 weight 1 nexthop via $P2 dev $IF2 weight 1
```

---

### Post by megamanexent on 2010-08-19
> **anthonyj460 said:**
> it may be a little late for you. and i havent actually tried this myself. i mearly have been curious as to how its done and this is what i keep finding. so here is a script that i got from [[COLOR="red"]here[/COLOR]]("http://www.go2linux.org/load-balance-traffic-for-two-isps-with-linux"). and this is a good place for most routing stuff [[COLOR="Red"]here[/COLOR]]("http://lartc.org/lartc.html")

```
#!/bin/bash -v
#just to be clear IF1 corresponds to P1, P1_NET, and IP1
# IF2 corresponds to P2, P2_NET, and IP2


#IPs of your device connected to the internet

IP1=190.84.224.246
IP2=190.156.148.160

# For Dynamic Connections (change 190.84. to match the beginning of your ip connected to the intenet)
#IP1=`ifconfig | awk -F: '/190.84./ {print $2}' | awk '{ORS=" "; print $1}' | awk '{print $1}'`
#IP2=`ifconfig | awk -F: '/190.156./ {print $2}' | awk '{ORS=" "; print $1}' | awk '{print $2}'`

#Your Gateways (type route in terminal it should be in the same line as default)

P1=190.84.224.1
P2=190.156.148.1

#Your Subnets
P0_NET=192.168.0.0/16 # your local network subnet, but i dont think you are sharing...
P1_NET=190.84.224.0/24 # Part of your gateway, P1 but replacing the 1 at the end with 0/24
P2_NET=190.156.148.0/23# Part of your gateway, P2 but replacing the 1 at the end with 0/23

# NICs your internet interfaces

IF1=eth0
IF2=eth1

ip route add $P1_NET dev $IF1 src $IP1 table T1
ip route add default via $P1 table T1
ip route add $P2_NET dev $IF2 src $IP2 table T2
ip route add default via $P2 table T2

ip route add $P1_NET dev $IF1 src $IP1
ip route add $P2_NET dev $IF2 src $IP2

#ip route add default via $P1

ip rule add from $IP1 table T1
ip rule add from $IP2 table T2

ip route add $P0_NET dev $IF0 table T1
ip route add $P2_NET dev $IF2 table T1
ip route add 127.0.0.0/8 dev lo table T1
ip route add $P0_NET dev $IF0 table T2
ip route add $P1_NET dev $IF1 table T2
ip route add 127.0.0.0/8 dev lo table T2

route del -net 0.0.0.0 netmask 0.0.0.0 dev $IF1
ip route add default scope global nexthop via $P1 dev $IF1 weight 1 nexthop via $P2 dev $IF2 weight 1
```
Thank you! It's not really too late.I have to check this out. Looks good.

---

### Post by pudgypaw on 2010-09-03
Taken from this thread:

telecomando@
[http://ubuntuforums.org/showthread.php?t=1008567](http://ubuntuforums.org/showthread.php?t=1008567)

You can't do this. You can do this with a T1 line and it is called BONDING. 1 IP shared across multiple T1 connections and is very expensive and has to come from your ISP. Verizon, ATT, Speakeasy anyone who provides T1's can do this.
With 2 cable modems you are going to have 2 IP addresses. There is no way to bond that.
The only thing you could do is LOAD BALANCING. Where you have a router in place that balances the traffic across the 2 connections. So if you have 2 5Mb connections and you balance them you'd still have 2 5Mb connections, not 1 10Mb connection. This is helpful when you have a lot of users behind on one network, they all would get decent speed but no one would get anything faster than 5Mb and traffic would be spread across the 2 internet connections. PFSense firewall can do this if you really want it but it will be of no benefit if it is only 1 computer behind the router. But there are other problems that come with this that you would have to deal with. HTTPS Sessions and other secure channels that might get confused seeing traffic come from a different IP then where it originated from.
But that's a whole other discussion.

-------------------------------

My own journey to aggregate my home ATT cable and my tethered Nexus One initially led me to this current thread and ended at the thread I quoted above. I know for a fact that each new internet connection serves up their own IP (in my case, my ATT router and my NexusOne). I thought it was possible to "torrent-ize" your connection because we deal with packets. But telecomando alerted me to the fact that the destination server needs to know what you're doing too. How can a server somehow know that packets coming from 2 different IP's should be combined and treated as one?

Perhaps in the future, we can create "IP-Aggregate" trackers shared between client and server, similar to a "torrent tracker" shared between clients. Since we were able to do this with torrent P2P technology, it should be theoretically possible for packet streams as well. But until we get enough users wanting to combine internet pipes, I don't see any one team going after this need anytime soon. As I'm not exactly skilled in this area, I would have to ask the rest of the open source community what they think...

And as telecomando also mentioned, load balancing is pointless on one computer, as it will simply fixate on the bigger internet pipe.

As of now, I don't think what we want to do is possible purely based on current internet protocols. But if such a protocol is developed, it would surely revolutionize our interface to the internet. A plug-and-play Multi-TCP/IP protocol allowing us to speed up connections by attaching smart phones to computers on the fly, just like plugging in flash drives to increase RAM and speed up PCs.

-pudgypaw

---

### Post by megamanexent on 2010-09-07
@[anthonyj460]("http://ubuntuforums.org/member.php?u=867474") I wasn't able to use the script to do anything useful. At last, it seems kind of impossible.
@[pudgypaw]("http://ubuntuforums.org/member.php?u=173584") Ahh. I see, what I really want to do was exactly what you tried to do(torrent-ize the connections). Also, as you stated, this may never happen (unless we push for development, e.g we go out and code it). Well it was good while it lasted. Thanks for your input.

I am not going to mark the thread as solved as it might one day help someone else in implementation or realizing it's currently impossible.

Thank you, FOSS community and Ubuntuforums!

---

### Post by BkkBonanza on 2010-09-07
See here,

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

Bonding is one method. The mode selected affects how the routing is managed.
Another method is using routing tables, as described in this link below. I've done it this way successfully before using this tutorial,

[http://lartc.org/howto/lartc.rpdb.multiple-links.html](http://lartc.org/howto/lartc.rpdb.multiple-links.html)

---

