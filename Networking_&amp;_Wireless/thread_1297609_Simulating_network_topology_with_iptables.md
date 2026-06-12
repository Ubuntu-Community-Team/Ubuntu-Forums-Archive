---
title: "Simulating network topology with iptables"
date: 2009-10-21
forum: Networking &amp; Wireless
---

### Post by htpw16 on 2009-10-21
Hello all,

I am trying to simulate a network topology by blocking certain clients from seeing each other directly. However I am a little stumped. The way I was blocking certain clients was by using:

iptables -A INPUT -s x.x.x -j DROP

This however, simply blocks all communication between the clients in question. Instead of completely blocking, I would like the client to look at its routing tables to see how to reach the other computer. How can I go about doing that?

Thanks for your help and suggestions.

---

### Post by htpw16 on 2009-10-22
Any ideas or suggestions?

---

