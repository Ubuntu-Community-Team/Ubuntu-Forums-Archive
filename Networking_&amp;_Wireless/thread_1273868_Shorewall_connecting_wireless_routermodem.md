---
title: "Shorewall connecting wireless router/modem"
date: 2009-09-23
forum: Networking &amp; Wireless
---

### Post by clivelr on 2009-09-23
Hi,

I am by no means a network expert, so although this might be a simple question to most people - I haven't been able to find an answer (or just misread the answer staring me in the face).

I am busy setting up shorewall on my ubuntu 9.04 machine. This machine connects to the netgear wireless router & modem which in turn connects to the internet.  This is fine, however I have my family also connecting to the netgear router/modem and I would like to allow them access to my machine, but filter out the rest of the world. The netgear wireless router assigns all connecting machines dynamic IPs on the 192.168.0.* range.

So for example:
Netgear router: 192.168.0.1 (Wireless Interface) 
Netgear router External IP: 203.66.12.104 (External IP from ISP is not static)
Me: 192.168.0.10   on wlan0
Bob: 192.168.0.11
Mary: 192.168.0.12
Jane: 192.168.0.25
Paul: 192.168.0.30
(Not real names :)  )

I understand that the netgear router is seen to shorewall on my machines as the "net" zone, and everything coming from there including other 192.168.0.* machines fits into this zone.

I would really appreciate some pointers or examples on where/how to setup shorewall for this setup.

Thanks in advance
Clive

---

