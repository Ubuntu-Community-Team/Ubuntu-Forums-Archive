---
title: "ufw blocking outgoing traffic to ip address"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by bagpussnz on 2009-09-06
Hi,
I want to block all outgoing traffic from my ubuntu 9.04 laptop to a particular ip address.

I have tried...

ufw deny from 0.0.0.0/0 to 10.240.1.104
and
ufw deny from anywhere to 10.240.1.104

but I can still access the machine (10.240.1.104)...
telnet 10.240.1.104 389
Trying 10.240.1.104...
Connected to 10.240.1.104.
Escape character is '^]'.
^]
telnet> quit
Connection closed.



I have tried restarting ufw and I see the rule in my iptables...

Chain ufw-user-input (1 references)
target     prot opt source               destination         
DROP       all  --  anywhere             10.240.1.104

What am I doing wrong?

Regards,
Ian.

---

### Post by nandemonai on 2009-09-07
Is there an allow rule that is higher in the chain that may be over-riding that deny rule?

---

### Post by elusivespoon on 2010-12-16
Try saying "ufw reject **out** from ..." UFW automatically sets the direction as "in" if the direction is not specified, so you only block incoming traffic. Seems like it would make more sense to apply it to both incoming and outgoing traffic instead, but that's what it does.

---

