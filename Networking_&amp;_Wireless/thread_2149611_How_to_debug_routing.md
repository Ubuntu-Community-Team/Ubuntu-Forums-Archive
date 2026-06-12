---
title: "How to debug routing?"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by nayuta on 2013-05-29
I have three networks. 1 and 2 are connected and 2 and 3 too. 2 is a connection network. 

There is one computer in network 1 and 2, it should route the traffic from computers in network 1 to network 3, and a computer in network 2 & 3 which should do the routing in reverse direction. The goal is that all computers from networks 1 and 3 can see each other and communicate.

Ping from network 1 to 3 (and reverse) does not work. The packets just get lost, no error.

I know how to use route, ping and ifconfig but I'm not able to figure out why this doesn't work. Is there a way to figure out at which stage the packet gets lost? Or what goes wrong in the routing? How can I see where the incoming traffic gets redirected to? Which tools should I have a look at? I just want to see more, to get an idea what's going wrong. At the moment, I just use ping to diagnose networking failures. I also know tcpdump, but I rather want to use something with less output...

---

### Post by nayuta on 2013-06-03
I got quite far with looking at the routing tables (route, route -n), modifying them (route add and route del) and observing traffic for specific interfaces (tcpdump -i eth1). Also, one time I forgot that to answer a ping, the reverse route has to work, too. 

Also: Google.

---

