---
title: "Connection lost after router restart"
date: 2010-08-11
forum: Networking &amp; Wireless
---

### Post by Mindgamer on 2010-08-11
My ISP pushes software updates occasionally to my router. This also forces the router to restart. When the router restarts, my ubuntu box loses its network connection and does not automatically restore it after the router comes back online.

How can I configure ubuntu to restore the connection once it is available again? It happens on my windows workstation...

I am using ubuntu on a box with no screen / keyboard / mouse - it serves as a fileserver and I remote desktop in. Obviously if the box drops the connection it is a major annoyance.

I am using version 9.10

Thank you.

---

### Post by sanderj on 2010-08-11
Good question! I have the same problem.

It seems Ubuntu will only refresh the network setting after a physical cable disconnect on it's own side or a manual network restart, and not after an inactive router/modem.

Strange.

Workaround: run a script that periodically/continuously checks the network or internet connectivity, and if it's absent, restart the network (/etc/init.d/network restart - from the top of my head).

HTH

---

