---
title: "Block IP forwarding to one specific interface"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by Jorgje on 2012-11-24
Hi everybody,

I have an Ubuntu machine that has two phyisical network interfaces (eth0 and eth1), connected to two phyiscally separated networks. The machine also runs a pptpd server. In order to make the pptpd server connect with the network on eth0, I had to enable IP forwarding in /etc/sysctl.conf by adding the following line:

```
  net.ipv4.ip_forward=1
  
```This makes the pptpd server work the way I want. But, if I understand correctly, it will also create the possibility to access the network on eth1 from eth0 and vice versa by using the machine as gateway, because IP forwarding is enabled.

I am looking for a possibility to block IP forwarding to and from eth1, while leaving the IP forwarding between eth0 and the pptpd server intact. Does anybody have experience on how to do this?

---

### Post by Doug S on 2012-11-25
I think you would just need a specific IP tables rule to prevent the traffic.
It would not be easy for me to setup my test computer to verify an answer for you, but I think something like (I didn't even test the syntax):```
sudo iptables -A FORWARD -i eth0 -o eth1 -j DROP
sudo iptables -A FORWARD -i eth1 -o eth0 -j DROP
```But give us some more info to be able to help further, such as your current iptable rules set, so we know exactly where to put the rules and or if they need to be changed.
 
Edit: I managed to sort of test this on one of my test computers. I think what I said above will do what you want. Also know that the various computers on the two sub-nets would also have to know how to route the traffic. What I mean is that I had to add a route so as to direct the packets from test computer 1 towards test computer 2, which had the two NIC cards, to get to test computer 3 on the other sub-net. Example:```
sudo route add -net 192.168.222.0 netmask 255.255.255.0 gw 192.168.111.112
```Only then could I test blocking the packets.

---

