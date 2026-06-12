---
title: "PPPoE weird problem: appearing more ppp connections, but network doesn't work"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by the_witch on 2009-01-09
Hi all :)

I have this problem: after I used pppoeconf to configure my connection (more times because my network was running just for 1 minute than went down), I saw in the graphic mode that I had 6 or seven pppconnections, plus my wired one. So I ran ifconfig and besides the loopback interface and the eth0, I had ppp0, ppp1, ppp2, ... to ppp6. ??!! So I tried to delete ppp6 or any of the ppp1 - ppp6 ifaces, but it told me that they don't exist. So I ran sudo poff -a. All ppp connections deleted, but afterwards I ran sudo pppoeconf again once, and there were ppp0 and ppp1 connections appearing in the graphic netw. conf menu and when running ifconfig also:

eth0      Link encap:Ethernet  HWaddr ...  
          inet6 addr: .. Scope:Link
          ....

lo        Link encap:Local Loopback  
          .......

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:70.114.129.72  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          ....

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:70.114.129.39  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          ..

:~$ sudo poff ppp1
/usr/bin/poff: I could not find a pppd process for provider 'ppp1'. None stopped.

So then I tried to delete ppp0 and it worked, but I still have the non-existing ppp1:

:~$ sudo poff ppp0
:~$ ifconfig
eth0   
lo       
ppp1      Link encap:Point-to-Point Protocol  
          inet addr:70.114.129.39  P-t-P:10.0.0.1  Mask:255.255.255.255
          ....

:~$ sudo poff ppp1
/usr/bin/poff: I could not find a pppd process for provider 'ppp1'. None stopped.

And my network connection doesn't work more than 1 minute before breaking down. I have to continuously run sudo /etc/init.d/networking restart. Can someone tell me what's happening? how do I create just one ppp connection and save it after running pppoeconf just once? Maybe it is a ppoe bug? where do I report it?

And also would like to mention that this wasn't happening yesterday before downloading the updates for ubuntu.

And also some other info (probably not relevant): I am using a Lenovo 3000 N100.

Thanks.

---

### Post by manadi on 2009-01-09
What modem are you using?

---

### Post by the_witch on 2009-01-09
It's not about the modem. I don't use a modem, but the direct cable. Fiberlink.

---

### Post by manadi on 2009-01-09
Ok, so where do you plug the cable?

also post o/p of

lshw -C network

---

### Post by the_witch on 2009-01-10
Hey, first of all thanks for your replys.
It's not about the modem or cable. I use the direct cable.
But I solved this weird prob by:

1. adding this line to the /etc/network/interfaces

pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

so now I have:

auto ppp0
iface ppp0 inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider ppp0

2. deleting all ppp connections with poff -a

and then just restarting the network connection from command line ( sudo /etc/init.d/networking restart ), without using pppoeconf after, and it works fine now.
So how do I mark this post as solved? :)

---

