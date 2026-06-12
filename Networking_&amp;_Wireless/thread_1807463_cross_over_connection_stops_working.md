---
title: "cross over connection stops working"
date: 2011-07-19
forum: Networking &amp; Wireless
---

### Post by dsupriya on 2011-07-19
I have one Ubuntu PC connected with another CPU (CAMAC Controller) by a crossover ethernet cable. I have established a network connection specifying static IP address for both the boxes. I could check the connection by ping. 
Now I have a code which checks the interrupt from the controller and reads the data. The code has an infinite loop and should keep on going. But my code here works for some time and stops at some point. If I end the program (^C) and start it again, it starts working.

---

### Post by jmoorse on 2011-07-19
Why don't you run a constant ping from Ubuntu in another window to see if the problem is actually the network?  If pings fail when the program locks up, they we have a network problem.

---

