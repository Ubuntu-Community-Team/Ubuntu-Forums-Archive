---
title: "mapping an ip address to other ip"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by azzamite on 2009-03-27
Hi there
In short, this is what I want to do in my laptop.
Every time something try to access the ip 10.10.10.10 (which is NOT in the LAN)
it must be redidected to other ip, lets say google.

I tried editing /etc/hosts, adding
[www.google.com](www.google.com) 10.10.10.10
[google ip] 10.10.10.10
(yes, I inverted the thing but didn't work)

I also tried this [http://www.shorewall.net/FAQ.htm#faq1g](http://www.shorewall.net/FAQ.htm#faq1g)
but didn't work either.

Any thougts?


--An explanation of my problem follows... you may skip it--


I have to download stuff from a maven repository from a server
which is accesible from both (MS) VPN and internet.

But the fact is that every time maven tries to acces the server
using **the IP of the VPN** instead of the public IP.
So I need to map the VPN address to the public address.

The last option is to edit every file maven downloads every time
I try to do something... but if I where to do that, my part of the
project would not be compatible with everyone else's.

And last, I haven't been able to connect to the VPN from here (sometimes not even from windows!).

---

