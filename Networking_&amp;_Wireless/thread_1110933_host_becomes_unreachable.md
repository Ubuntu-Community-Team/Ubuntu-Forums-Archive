---
title: "host becomes unreachable"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by jjrp78 on 2009-03-30
Hi all,

I have an ubuntu box running an open ssh server and a gnump3d serve that I use to stream music to work. 

Every morning I turn it on, check that it works from other machine in my own LAN and go to work. By the time I get to the office something happens that I just can't connect (from my router I am forwarding both ports 22 and 8888 to the machine so that is not the problem). 

When I come back home I find the server up and running, it has an IP an all. From the machine I can access internet I get responses when I ping any server like yahoo, google etc but I just can not connect to it from other machine using ssh or the web interface for gnump3d.

 The machine doesnt even responds to a ping from another computer in the same LAN. If I restart the machine it works fine again.

Any ideas how to trouble shoot?

UPDATE: I was wrong, when the server becomes unreachable it can't access internet, doesnt manage to ping any server, but it still has an ip address in the eth0 interface

---

