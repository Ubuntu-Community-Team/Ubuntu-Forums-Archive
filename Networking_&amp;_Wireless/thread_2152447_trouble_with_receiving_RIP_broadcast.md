---
title: "trouble with receiving RIP broadcast"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by lux11 on 2013-06-07
Hi all. My question is similar to my recent to linuxforums but focused on Ubuntu. 

Briefly, I have a program that has a built-in RIP client that collects routing information from a host that broadcasts periodically. All has been running well up until a week ago when the routing tables in my program ceased to be updated. I have used tcpdump to verify that the RIP broadcasts are indeed being sent, not being blocked by a firewall,  and that they are routed to the linux box on my LAN where the program resides. So I know the source of the RIP broadcasts is not the issue nor is my ISP or my main router. 

SO, here's the question. Is it possible that due to ongoing Ubuntu updates, that some change has recently been made that would cause a block in the way my program processes the RIP function? I know multicast is involved (224.0.0.9) but I do not know enough about how multicast works to even ask a good question. I'm looking for ways to diagnose this problem so I can drill down and fix it. 

I am currently running Ubuntu 12.04.2 LTS.

Thanks for suggestions. Until then, I continue my research.
Lux

---

### Post by lux11 on 2013-06-09
SOLVED
As it turns out, I do not beleive this problem was related to any updates of Ubuntu.

The program that receives routing information through the RIPv2 broadcasts has an IP address on my LAN and that IP needed to have a 'static route' added to my router with the IP of the linux box which serves as its gateway. And key to setting this up for a multicast is to make sure the subnet mask is [255.255.255.255]("tel:255.255.255.255") . Although this setting had already been made in the router, I found that I had to remove it and then create it again in order for it to work. Now I can see the multicast IP (224.0.0.9) being broadcast when I do a wireshark capture and the routing tables of the program populating correctly.

---

