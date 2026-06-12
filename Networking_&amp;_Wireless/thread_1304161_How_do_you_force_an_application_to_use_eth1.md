---
title: "How do you force an application to use eth1 ?"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by boondocks on 2009-10-29
We have 3 different custom developed applications.
They are running on one Ubuntu system.
This system is connected to 2 different networks via eth0 and eth1.

How do you make application 2 use eth1 ?
(By default, these 3 applications are using eth0.)

These applications require internet connectivity BUT do not have any network setting capability.

---

### Post by bribera on 2009-10-29
I'm not entirely sure how you'd specify an individual interface. Have you considered bonding the two?

Bonding will make the two interfaces act as one, and the kernel will load balance between the actuall NICs for you. This is nice, since your code can be agnostic of the number of interfaces.

Here's a howto, if that will suit your needs:

[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

### Post by boondocks on 2009-10-29
Nice, but Bonding will not apply in this case.
Why?  Because ...
> **bribera said:**
> Bonding will make the two interfaces act as one, and the kernel will load balance between the actuall NICs for you. This is nice, since your code can be agnostic of the number of interfaces.
So instead of just application 2 using eth1, all the applications will end up using eth0 and eth1.

---

### Post by Lars Noodén on 2009-10-29
It depends on the application.  If it is some kind of server application, usually the configuration allows you to specify which interface they listen on or to an address bound to that interface.  

For an example of the latter:
[http://httpd.apache.org/docs/2.2/bind.html](http://httpd.apache.org/docs/2.2/bind.html)

Or you can make a terrible hack using iptables' --uid-owner or --gid-owner, which would be useful in binding all processes by a given user or group to a specific interface.  That would require some additional planning for which user or group the processes run as.

---

