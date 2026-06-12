---
title: "How do I use external transparent proxy for a single host?"
date: 2010-07-24
forum: Networking &amp; Wireless
---

### Post by codezion on 2010-07-24
Hello,
 
I have searched for this quite a bit but my lack of knowledge of  IPTables makes me doubt whether I have found a solution or not. I have  very light experience with IPTables as well. So I thought I'd ask here.
 
Basically, what I am trying to do is use an external transparent proxy  for only one of the hosts on my internal network. For example, for an  internal host of 192.168.1.8, I want to send all internet requests for  ANY port to a proxy server out in the internet at 238.34.232.7 / port:  8080. All other hosts would use the internet without using any proxy  server.
 
Is IPTables the way to set this up or is there an easier option? Could someone please help me figure out how to do this? 
 
Thanks a lot!

---

### Post by codezion on 2010-07-28
I researched iptables and came up with something like below. I thought it would be a matter of a simple source and destination IP and forwarding all packets for all ports. But this doesn't work for some reason. Any idea why?

```
#!/bin/sh
 MEDIA_IP=192.168.1.129
 PROXY_IP=85.224.23.2
 PROXY_PORT=80
 LAN_NET=192.168.1.0/24

 iptables -t nat -A PREROUTING -i tun0 -s $MEDIA_IP -d $LAN_NET  -j ACCEPT
 iptables -I FORWARD -i tun0 -o br0 -s $MEDIA_IP -d $PROXY_IP --dport $PROXY_PORT -j ACCEPT

```BTW, I don't think this matters but my iptables box is my dd-wrt router. Any help would be greatly appreciated.

---

