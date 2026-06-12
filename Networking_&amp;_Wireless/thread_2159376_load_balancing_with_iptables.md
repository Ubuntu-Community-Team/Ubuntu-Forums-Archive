---
title: "load balancing with iptables"
date: 2013-07-02
forum: Networking &amp; Wireless
---

### Post by Qest on 2013-07-02
I am trying to set up my ubuntu server so that whenever someone connects to port 9050, the request is redirected to a different port (one of 9051, 9052, 9053, ..., 9060, chosen randomly).

I've added this rule:

iptables -t nat -A PREROUTING -p tcp --dport 9050 -j REDIRECT --to-ports 9051-9060 --random

But it doesn't seem to be working for me.

Does anyone know where I am going wrong?

---

### Post by Doug S on 2013-07-03
The syntax of your command seems correct. Perhaps you need to specify an interface, such as:```
iptables -t nat -A PREROUTING -p tcp [COLOR=#ff0000]-i eth0[/COLOR] --dport 9050 -j REDIRECT --to-ports 9051-9060 --random
```Also, could you tell us a bit more about the bigger picture for your application? Since your subject line says "load balancing", I was wondering if there is some further packet manipulation after this, perhaps forwarding to an array of different servers based on port number, and maybe the problem is elsewhere in the overall iptables rule set.

---

