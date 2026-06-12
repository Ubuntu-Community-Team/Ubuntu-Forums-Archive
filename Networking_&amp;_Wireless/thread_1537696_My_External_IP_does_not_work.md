---
title: "My External IP does not work"
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by hr.asadi on 2010-07-23
Hi,

I know that the topic is not new but I couldn't solve it in no way.

I am running an Ubuntu 10.4 box with all ports forwarded on an internet router. The point is I can ping my PC with its external IP but no other services are accessible through it.

I have also checked my iptables rules. It's completely flushed and the default rule is set to ACCEPT.

The worst thing is that when I boot my box with windows XP, it is completely accessible by its external IP and I could successfully initiate a remote desktop connection to it over the net.

Is there any ideas? It is annoying!!

---

### Post by Iowan on 2010-07-24
What services have you tried?
(Silly question, but are they installed?)

---

### Post by hr.asadi on 2010-07-25
I have tried apache on Port 80 and ssh on 22. And yes! they are installed :)

---

### Post by Iowan on 2010-07-25
Reason for asking - "most" clients come pre-installed, but the server portion must be added. One might assume that if you can connect to another machine via SSH that you could connect to the machine via SSH... but the server must be added.
Apache... most wouldn't assume that a web server comes pre-installed - you'd know if you installed it.

Are the services running? Can you connect from localhost or another machine inside the net (using local address)?  I realize they're different protocols, but it's curious that ping (and only ping) works. :-k

---

### Post by hr.asadi on 2010-07-26
Well, what can I say is all the servers I have mentioned are up and running. Believe me! I am using them almost everyday. ;)

By the way, I have double checked this issue with my network administration and he claimed that issue raises because my valid IP is behind two NAT servers. In other words my packets are masqueraded twice to get to my PC. He told that the same issue is also happening in Windows 7 but win XP works well. 

He have checked the configuration a couple of times and he said that everything is OK (and my Ubuntu box works well) if only one NAT server routes my traffic. 

I don't know anything about the implementation of networking but is there some algorithms or policies are applied to both Ubuntu and Win7?

---

