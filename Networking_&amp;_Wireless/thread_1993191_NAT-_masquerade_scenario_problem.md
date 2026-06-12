---
title: "NAT- masquerade scenario problem"
date: 2012-06-01
forum: Networking &amp; Wireless
---

### Post by CheerfulSonya on 2012-06-01
Hi to all...I have asked all my friends but no one didn't know to help me :( ...so i was surfing a bit and found out this forum :P ...i have seen that many problems were solved here, so i hope that my problem will be one of them ...  :P:P:P   


So, anyway let me tell my problem (immediately in my first post hahaha)...
well, i have problem with one simple MASQERADING scenario...really need to help... 
On one computer pc1 (let's call it router) i need to open a new subinterfaces (exp. eth0:1) where is possible to communicate with rest of the my LOCAL AREA NETWORK...I need to set up the NAT on my pc1 (router) and enable another computer PC2 (let's call it user) to communicate with rest of Local Network... Also is necessary to configure the PC2 (user) to use PC1 (router) as gateway (hint: default gateway). And after all that when i check the communicate between PC2 (user) with rest of LAN (with ping) i need to get source address of PC2 (router) in ICMP packets on destination PC. 


And all computers in my Network are have install only one network Interface...
Well i also post pic here how i see the problem (maybe i didn't drew the best but i think that is clearly what i want to say haha)...so i hope that will help to you... 


and I also type this commands


//PC2
route add default gateway 192.168.0.105 eth0


//PC1
Ifconfig eth0:1 192.168.0.105 netmask 255.255.255.0 up
Ifconfig eth0:1 192.168.1.105 netmask 255.255.255.0 up
iptables -t nat -A POSTROUTING -d 192.168.0.105 -j MASQUERADE
iptables -A FORWARD -s 192.168.0.105 -d 192.168.1.105 -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD - s 192.168.1.105 -d 192.168.0.105 -j ACCEPT
iptables -t nat -A POSTROUTING -s 192.168.0.105 - j SNAT - - to-source 192.168.1.105 

and after all that didn't work... i&#8217;m so lost... ](*,)

don&#8217;t know what to do anymore...


Thanks for any help what i get...

---

### Post by HermanAB on 2012-06-02
Here is a simple example:
[http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html](http://www.aeronetworks.ca/howtos/Laptop-NAT-Howto.html)

---

### Post by CheerfulSonya on 2012-06-04
Many thanks for your help...Much appreciated that...
the problem was been that i forgot to enable the ip forwarding with command 

1 > /proc/sys/net/ipv4/ip_forward

thanks again...

---

