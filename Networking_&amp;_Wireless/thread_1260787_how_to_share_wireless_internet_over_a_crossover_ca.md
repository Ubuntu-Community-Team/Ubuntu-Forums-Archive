---
title: "how to share wireless internet over a crossover cable?"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by VobSub on 2009-09-08
I need help with my laptop. Today i finally got rid of xp and installed ubuntu 9.04 on my dell inspiron 8200.  With xp i had it set up so the laptop got the internet from the router via a netgear wireless card.  I routed the internet through a crossover cable to my desktop with ubuntu 9.04.  Now the two computers won't even ping each other.  I am wondering how to set up my laptop to rout the internet to my desktop.

---

### Post by jerrrys on 2009-09-08
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

more here

[http://www.google.com/search?q=internet+connection+sharing+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=internet+connection+sharing+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by Iowan on 2009-09-08
At the bottom of the (first) aforementioned link is [this ]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") one for sharing via wireless.

---

### Post by VobSub on 2009-09-08
I can't even get the laptop and computer to ping each other.  It says network unreachable in terminal

---

### Post by Iowan on 2009-09-09
What are IP addresses for each machine? (**ifconfig -a** and **ipconfig**

---

### Post by VobSub on 2009-09-15
okay i got the computers to ping but i can't get them to share internet.  
                                                  [https://help.ubuntu.com/community/In...nectionSharing ]("https://help.ubuntu.com/community/Internet/ConnectionSharing")

Every time i use this link i get to 

[LIST]
[*]Edit /etc/sysctl.conf and add these lines:
[/LIST]

net.ipv4.conf.default.forwarding=1
net.ipv4.conf.all.forwarding=1

But every time i try to edit it and save.  It says that i don't have permission to change it.  Something about root is the owner.  This is my laptop and no one else uses it.
What is root? and how to i get around it?  Also is there another way to share internet?
Sorry for the late reply.

---

