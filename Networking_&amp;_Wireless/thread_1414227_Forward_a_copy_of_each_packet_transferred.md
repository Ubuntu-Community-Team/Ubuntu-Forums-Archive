---
title: "Forward a copy of each packet transferred"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by hammad1337 on 2010-02-23
I manage a small home network of 5-6 PCs and other devices. One of the PCs is used as a multipurpose server, as well as the gateway to outside.

Sometimes, I need to know what traffic goes in/out of my network (for troubleshooting, etc).

Is there a quick and dirty way to forward a copy of all the packets on the external interface to my own ip when I want to?

Thanks for you time.

---

### Post by koszta on 2010-02-23
add an Iptables rule:
iptables -t nat -A PREROUTING -i $THE_SOURCE_INTERFACE -j DNAT --to-destination $YOUR_BOX_YOU_WANT_TO_FORWARD_TO

This is basically just traffic forwarding not actually copying it. 

This is already pretty dirty... (it is very hard to actually do what you want to since iptables and linux in general is/was always meant to be safe and you are trying something what the programmers try to avoid....
There is a iptables mood called xtables and there is a howto on how to REALLY CLONE upd packets: 

[http://www.bjou.de/blog/2008/05/howto-copyteeclone-network-traffic-using-iptables/]("http://www.bjou.de/blog/2008/05/howto-copyteeclone-network-traffic-using-iptables/") BUT I dont know about any other way how to clone tcp packets...Only forward... if that is enough for you tho

---

### Post by koszta on 2010-02-23
PS.. man just use wireshark for this...It works the way that it puts your NIC in "promiscuity" mode - meaning that it also receives packets for other machines...It is far better than just copying the packets. Wireshark has implemtation of tcpdump (which you might also use)

---

