---
title: "Firefox etc stops accessing the internet"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by ITT1 on 2009-03-02
I have a dual boot ACER machine ubuntu 8.10/ Vista. I have two Netgear USB dongles WG111v2 and WG111v3.

I let ubuntu install it's choice of drivers for whichever dongle I'm using. 

It usually starts working well, and then I notice that Firefox stops loading the webpages when I click on a link. Emails (Evolution) and system update are affected too. So basically, the computer is accessing the internet, and it's working fine, then for no reason it stops. it says "Firefox can't find the server at..." If I wait long enough, it starts again.

BUT, the NetworkManager applet shows typically 66% or more and I can access other computers on my home network quite happily. As well, other computers on the network (one ubuntu and one XP) access the internet perfectly well so the 2Wire Gateway seems OK too.

Finally, if I boot Vista it works fine, though slowly (which is why I'll continue to use ubuntu and put up with the fuzzy fonts)
What's going on?? 

Is there some configuration I need to do for Firefox? Choose and install the driver myself?? It has all the updates installed. 

Any ideas appreciated!!

---

### Post by Korcia on 2009-05-08
Try decreasing the following parameters in firefox (about:config):

- network.http.max-connections (<=48 )
- network.http.max-persistent-connections-per-proxy (<=12 )
- network.http.max-persistent-connections-per-server (<= 8 )
- network.http.pipelining.maxrequest (<=8 )

It could be that the nat table of your router becomes overloaded.

---

### Post by superprash2003 on 2009-05-08
post output of **ifconfig **from the terminal.

---

### Post by ITT1 on 2009-05-09
Thanks for the help. I moved the dongle and the router much closer so that the signal is much stronger. Works fine now.

> **ITT1 said:**
> I have a dual boot ACER machine ubuntu 8.10/ Vista. I have two Netgear USB dongles WG111v2 and WG111v3.

I let ubuntu install it's choice of drivers for whichever dongle I'm using. 

It usually starts working well, and then I notice that Firefox stops loading the webpages when I click on a link. Emails (Evolution) and system update are affected too. So basically, the computer is accessing the internet, and it's working fine, then for no reason it stops. it says "Firefox can't find the server at..." If I wait long enough, it starts again.

BUT, the NetworkManager applet shows typically 66% or more and I can access other computers on my home network quite happily. As well, other computers on the network (one ubuntu and one XP) access the internet perfectly well so the 2Wire Gateway seems OK too.

Finally, if I boot Vista it works fine, though slowly (which is why I'll continue to use ubuntu and put up with the fuzzy fonts)
What's going on?? 

Is there some configuration I need to do for Firefox? Choose and install the driver myself?? It has all the updates installed. 

Any ideas appreciated!!

---

