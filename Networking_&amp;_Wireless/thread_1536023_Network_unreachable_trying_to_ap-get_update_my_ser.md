---
title: "Network unreachable trying to ap-get update my server, but laptop is fine"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by networkslave on 2010-07-21
Hi

I have searched the forum but do not find a solution that would fit my problem.  so I post this hoping not to annoy someone with a duplicate.

My 9.10 Ubuntu server is accessible from all local workstations running Ubuntu and MS.  All Ubuntu workstations can access the Ubuntu resource servers (on the internet) for software installations and updates but the server cannot.  I get the message.

W: Failed to fetch [path and IP address of the resource] connect (101. Network is unreachable)

I'm not using a proxy or firewall.
Server IP address with gateway and DNS configured manually.
DNS and gateway the same as workstations

My laptop and other workstations can traceroute the resource IP, but the server says NETWORK UNREACHABLE. and does not even go my local DSL switch (gateway).  

I can traceroute and ping any workstation on my local network from the server but any IP outside my local network is NETWORK UNREACHABLE.

Please help me resolve this without reinstalling Ubuntu (Like I do with MS to solve problems).  I want to install Squid proxy so that all wokstations can update from the proxy and not need to go out on the internet.

---

