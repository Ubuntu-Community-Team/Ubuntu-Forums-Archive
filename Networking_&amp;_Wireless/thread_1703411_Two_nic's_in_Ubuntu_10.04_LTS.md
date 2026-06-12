---
title: "Two nic's in Ubuntu 10.04 LTS"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by trentend on 2011-03-09
I am in the process of building a number of servers that need to be connected on one subnet for shared organisation wide services, and a separate subnet for each specific division.

I need to use separate nic's for each subnet that the server resides on.  Essentially for traffic routing reasons.  The shared subnet will be connected to the internet, have shared services (such as VoIP phones, printers, and backup through rsync).  Each division subnet has specific services for that business unit (file and printer serving, email, webservers).

I have two nic's in each server box.  Both are recognised, but only eth0 is configured after install.  If I attempt to setup eth1 on a different subnet this appears to work through the same nic as eth0.  This is something I don't want as I want to split out the traffic between the two nic's.

Clearly I'm doing something wrong, but there does not appear to be any coherent information available to achieve what I want.  Could anyone point me to an appropriate place?

Ultimately I need to route internet traffic, print to shared printers on the general services subnet and use this route to backup between servers, without consuming bandwidth on the specific division subnet/nic.

---

### Post by trentend on 2011-03-14
Can nobody offer any guidance?

---

### Post by mips on 2011-03-14
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

Old and few things have probably changed but have a look anyway.

---

### Post by YesWeCan on 2011-03-14
Have you considered using routers instead?
Discrete routers are a little more expensive than NICs but, in my experience, a whole lot less effort to configure.

---

### Post by pricetech on 2011-03-14
Routers do seem the best solution, assuming we're reading and understand what it is your trying to do.

More information might be helpful also, with some scenarios thrown in for clarification.

---

### Post by afilonov on 2011-03-14
> **trentend said:**
> I am in the process of building a number of servers that need to be connected on one subnet for shared organisation wide services, and a separate subnet for each specific division.

I need to use separate nic's for each subnet that the server resides on.  Essentially for traffic routing reasons.  The shared subnet will be connected to the internet, have shared services (such as VoIP phones, printers, and backup through rsync).  Each division subnet has specific services for that business unit (file and printer serving, email, webservers).

I have two nic's in each server box.  Both are recognised, but only eth0 is configured after install.  If I attempt to setup eth1 on a different subnet this appears to work through the same nic as eth0.  This is something I don't want as I want to split out the traffic between the two nic's.

Clearly I'm doing something wrong, but there does not appear to be any coherent information available to achieve what I want.  Could anyone point me to an appropriate place?

Ultimately I need to route internet traffic, print to shared printers on the general services subnet and use this route to backup between servers, without consuming bandwidth on the specific division subnet/nic.

I did something similar, successfully. What configuration do you have now (best of all, post your /etc/network/interfaces)

---

