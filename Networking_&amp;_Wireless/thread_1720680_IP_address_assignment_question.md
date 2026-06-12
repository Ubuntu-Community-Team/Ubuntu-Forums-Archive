---
title: "IP address assignment question"
date: 2011-04-03
forum: Networking &amp; Wireless
---

### Post by Nick Kruger on 2011-04-03
I'm sure this is a simple question.
 
I've got 1 physical ubuntu server.
 
I give it a static IP - 192.168.1.1
 
Now, **if **I add a web server, samba server, some other server - to the same physical box, **then** :
 
Do I give each server it's own IP :
 
127.0.0.1 localhost
192.168.1.1 jupiter.solarsystem 
192.168.1.2 web 
192.168.1.3 samba 
192.168.1.4 mail
 
Is this correct / not correct / optional / depends ??
 
Please set me straight on this topic.
 
Thank,
Nick Kruger

---

### Post by fela on 2011-04-03
No, you only have one IP address for the machine. Different services share the same IP but different ports. Also, there are some things like Apache that serve different stuff depending on the host name (so I could have [www.onesite.com](www.onesite.com) and [www.totallydifferentsite.com](www.totallydifferentsite.com) point to the same IP, however apache handles them differently and serves the correct site).

---

### Post by lisati on 2011-04-03
The normal practice is that one IP address gets assigned to one network connection. The different *services* (web site, email, ssh etc) are commonly handled by the use of *ports*, which work a bit like site-specific telephone extension numbers.

---

### Post by Nick Kruger on 2011-04-03
Thanks fela,
 
Yes, your reply makes perfect sense. I always thought 1 IP for each interface.
 
But, now I have seen "additional" interfaces being created for eth0 - eth0:0, eth0:1.
 
Why do this ? - I mean if you don't have to - as your answer suggests.
 
Nick

---

### Post by Nick Kruger on 2011-04-03
Thanks for putting my mind at rest. 
I'll continue with just the 1 ip address.
 
Nick

---

### Post by fela on 2011-04-03
> **Nick Kruger said:**
> But, now I have seen "additional" interfaces being created for eth0 - eth0:0, eth0:1.

That's strange - I've never seen that behaviour!

---

