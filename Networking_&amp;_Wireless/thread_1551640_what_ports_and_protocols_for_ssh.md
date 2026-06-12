---
title: "what ports and protocols for ssh"
date: 2010-08-12
forum: Networking &amp; Wireless
---

### Post by anonmars on 2010-08-12
Hello,

I have ssh running on port 22 and that is the only thing I want in/out of this particular box (ssh, scp).

But when I use iptables to set the default policies for INPUT, FORWARD, and OUTPUT to DROP and then allow 22:

iptables -I INPUT -p tcp --dport 22 -j ACCEPT
iptables -I OUTPUT -p tcp --dport 22 -j ACCEPT

ssh stops working.

What am I missing?

---

### Post by gombadi on 2010-08-12
> 
But when I use iptables to set the default policies for INPUT, FORWARD, and OUTPUT to DROP and then allow 22:

iptables -I INPUT -p tcp --dport 22 -j ACCEPT
iptables -I OUTPUT -p tcp --dport 22 -j ACCEPT

ssh stops working.


Outgoing packets are going to be coming from port 22 not going to port 22 so change --dport to --sport for the output rule.

---

### Post by anonmars on 2010-08-12
> **gombadi said:**
> Outgoing packets are going to be coming from port 22 not going to port 22 so change --dport to --sport for the output rule.

Gack. How embarrassing. Thanks much! Now it works!

---

