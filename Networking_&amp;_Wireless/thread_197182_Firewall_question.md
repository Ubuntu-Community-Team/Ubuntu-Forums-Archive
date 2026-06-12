---
title: "Firewall question"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by ironfistchamp on 2006-06-15
No don't worry I'm not asking for a firewall to be put into Ubuntu as standard. I am asking how the linux style firewalls compare to that of windows. In windows you need a firewall. You can block programs and ports and all that.

Can you do all this in linux? I know you can do ports but can you do programs? Is a firewall necessary? How secure are they? What kind of selection do we have? I know of IPtables but is there a graphical one?

Thanks

Ironfistchamp

---

### Post by kb3hkg on 2006-06-15
Yes you can do that in linux, though not with IPtables. A firewall is necessary on any machine connected to an external network in my opinion, it is just a lot safer.

How secure are they? well that would depend on how the firewall is configured and what it is letting through. There are many options for firewalls in linux, but most of the GUI's you will find are all just IPtables front ends.

---

### Post by ns2048 on 2006-06-15
IMO iptables is an excellent firewall. Much more flexible than anything in Windows. Take a look at Firestarter ([http://www.fs-security.com)](http://www.fs-security.com)). You can install it by running 'sudo aptitude install firestarter'.
--ns2048

---

### Post by Slim Odds on 2006-06-15
[quote=kb3hkg]Yes you can do that in linux, though not with IPtables. A firewall is necessary on any machine connected to an external network in my opinion, it is just a lot safer.[/quote] 
Most "firewall" software on linux is just a GUI frontend to hide all the details of iptables. iptables is where most of the real "firewalling" to going on.

---

