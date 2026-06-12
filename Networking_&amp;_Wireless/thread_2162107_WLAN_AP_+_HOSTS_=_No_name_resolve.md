---
title: "WLAN AP + HOSTS = No name resolve"
date: 2013-07-13
forum: Networking &amp; Wireless
---

### Post by joe500 on 2013-07-13
Hello,

I've a very simple question for you, but I'm very new to Ubuntu:P

I've a Ubuntu server running with a wlan adapter working in accesspoint mode. I can reach that network with other computers, but cannot use the name resolution of it.
For example my wlan card(of the server) has the ip: 192.168.0.3 I can type in that ip from a connected computer and get the appache test page which is exactly what i want.
But wehen I edit my hosts(of the server) to 192.168.0.3  sample-name and try to reach the same address by typing sample-name in the browser of the connected computer I get nothing.
On the ubuntu server itself the namersolution just works fine I tried it by typing ping sample-name and it worked.

can anybody please help me with that?

greetz Joe

---

### Post by praseodym on 2013-07-13
Check the /etc/hosts file:

[http://wiki.ubuntuusers.de/hosts#Namensaufloesung](http://wiki.ubuntuusers.de/hosts#Namensaufloesung)

1st grey box

---

### Post by joe500 on 2013-07-13
Thank you very much I was a bit confused about the other possibilities you have in the hosts:lolflag:

---

