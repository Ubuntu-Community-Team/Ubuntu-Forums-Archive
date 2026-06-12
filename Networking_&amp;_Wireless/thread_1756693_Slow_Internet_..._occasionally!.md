---
title: "Slow Internet ... occasionally?!"
date: 2011-05-12
forum: Networking &amp; Wireless
---

### Post by jazzman121 on 2011-05-12
Hi everyone!

I've been having this weird problem for a while now.

Every now and then (usually a week or more apart) parts of the internets are barely reachable for little old me. Loading sites with any browsers or wget will slow down to a halt, usually resulting in time outs - but only for some (most?) parts of the net. Some sites will continue loading just fine.
Google and sites associated with google are affected as are some others. Yahoo will still work in these occasions. But since every other site uses some portion of google's magic these days, browsing is basically right out.

Usually these episodes last a day. After that everything seems back to normal.

I don't think ipv6 is to blame, since resolving names works just fine:
```

wget google.com
--2011-05-12 20:36:23--  http://google.com/
Resolving google.com... 209.85.148.99, 209.85.148.103, 209.85.148.104, ...
Connecting to google.com|209.85.148.99|:80... 

```The address is resolved immediately, the connection takes forever though.

As you can imagine, this makes life rather hard.

Pinging my router works fine too:
```

ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=0.571 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=0.588 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=0.558 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=0.580 ms
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.558/0.574/0.588/0.020 ms


```The weird thing is this started happening a while ago and I'm using an altogether new computer now (installed 11.04 right when I got it). Other machines in the network seem to be affected aswell. 

Rebooting the router does not work. Neither does a cold reboot.

Any ideas?

---

