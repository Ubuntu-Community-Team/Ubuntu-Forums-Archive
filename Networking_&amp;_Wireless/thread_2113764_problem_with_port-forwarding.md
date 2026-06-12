---
title: "problem with port-forwarding"
date: 2013-02-08
forum: Networking &amp; Wireless
---

### Post by maja_ldm on 2013-02-08
hello everyone :)

I'm trying to open a port for p2p (Transmission or Deluge...)
I set up a static IP, filling the network connections menu with the data obtained through nm-tool (I had two DNS values I used the first one)
I manually opened a port in my router, following the instruction in portforward.com (port is 51-413)
I allowed an exception in the firewall, using gufw (for port 51413/tcp)
CanYouSeeMe.com tells me the port is closed
grc.com tells me the port is in stealth

distro is Ubuntu Lucid-Lynx, router is TP-Link TL-WR841N. 
btw, until a couple months ago I didn't use any port forwarding and the torrents worked without any problems.

---

### Post by BenWhitey on 2013-02-17
I'm having a similar problem. I can't open any ports on my system and no I do not have a router. I on an institution network and my computer is connected directly to the internet (on windows everything happens automatically once I add an exception for the windows firewall) but I can't seem to get it working in ubuntu 12.10.

Everything I've read says that all ports are opened by default in ubuntu but that does not seem to be the case. I've tried installing firewalls and adding exceptions but that doesn't do anything. I've tried with iptables and that didn't work

---

### Post by ahallubuntu on 2013-02-17
~

---

### Post by BenWhitey on 2013-02-17
I think that the problem is that the iptables rules aren't correctly setup to forward the port and to allow an incoming connection. I'm having the same problem in 12.10.

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere                     

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere     
```

I'm not sure how I should change my iptables to make it so that I can accept incoming connections more than what I've already changed. Any thoughts?

---

