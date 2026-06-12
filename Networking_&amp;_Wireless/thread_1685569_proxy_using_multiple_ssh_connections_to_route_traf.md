---
title: "proxy using multiple ssh connections to route traffic to the apropriate jump box"
date: 2011-02-10
forum: Networking &amp; Wireless
---

### Post by creatureofthedark on 2011-02-10
hey guys... sorry if this has alreay been covered hear... but i did a quick search and couldent find anything....


what i want to do is set up a proxy box on my network that has ssh connections to 3 diffrent jump boxes... so that computers on my network can use this proxy to access all servers behind the 3 jumpboxes without holding the 3 ssh tunnels itself..

example...

me types into browser 192.168.3.20 traffic gose from me to the proxy.. which then decides which ssh tunnel to send the traffic over.. and they sends it to the jumpbox wich sends the request to the server *[jump boxes are already set up to do this]*

[SIZE=1]*[have attached a diagram.... it apears ascii diagrams are hard to do in this forum....]*[/SIZE]


[edit] just a quick note... the proxy dosent have direct connection to these jump boxes... they are actualy accessed via the interent.... i just wasnt all that imaganative with IPs :P [/edit]
any ideas would be great :D

---

### Post by gmargo on 2011-02-11
I have done something similar using the **tinyproxy** package.  It is an http proxy that supports multiple upstream proxies.

---

### Post by creatureofthedark on 2011-02-13
hmmm looks interesting i will see if this dose what i need


thank you

---

