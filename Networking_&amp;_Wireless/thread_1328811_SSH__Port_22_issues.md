---
title: "SSH / Port 22 issues"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by mikelowell on 2009-11-16
Hi All,  
    I just installed 9.1 on my desktop, but it doesn't seem to be working properly. I can SSH into my mac from my linux machine no problem, but when I try to ssh into my the linux machine from the mac I get this instead:

port:22 Connection Refused.

I don't know what this means though or how to fix it.

Mike

---

### Post by ctyc on 2009-11-17
Have you tried to turn off your firewall?

---

### Post by Lars Noodén on 2009-11-17
> **mikelowell said:**
> but when I try to ssh into my the linux machine from the mac I get this instead:

port:22 Connection Refused.

I don't know what this means though or how to fix it.



It usually means either sshd is not running on your linux machine or your firewall is blocking port 22.  

Check to see that the package openssh-server is installed and running on your linux machine.  If yes to both, then check your firewall configuration.  If you wish to connect to ssh, then you should allow incoming TCP connections on port 22.

---

