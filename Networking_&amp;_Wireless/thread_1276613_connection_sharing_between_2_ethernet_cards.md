---
title: "connection sharing between 2 ethernet cards"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by dracule on 2009-09-27
Hello. 

I have my workstation set up like this:

[ethernet from wall] -> eth1 -> ubuntu 9.04 -> eth0 -> my laptop


so everything works in vista, but i dont know how to get connection sharing going for ubuntu. 

Currently i have

eth1 set up with DHCP

eth0 set as "share this connection" under ipv4 settings.



but my laptop is not getting an IP from eth0. (my laptop is configured to get the IP via DHCP)

any help?

---

### Post by DFlame on 2009-09-27
[A couple of suggestions](http://ubuntuforums.org/showthread.php?t=418446) :)

---

### Post by dracule on 2009-09-27
> **DFlame said:**
> [A couple of suggestions](http://ubuntuforums.org/showthread.php?t=418446) :)

I tried looking at those but they give like 100 steps to do. plus they are more than 2 years old and 9.04 was supposed to have simplified internet sharing.

---

### Post by DFlame on 2009-09-27
[Firestarter](http://www.fs-security.com/docs/wizard.php) may be able to set this up for you too. It's easily installed, though I have just linked to the relative part of the program.

I've not had to go through this before, so my ideas might not stick.

---

### Post by cariboo on 2009-09-27
Have a look [here]("https://help.ubuntu.com/community/Internet/ConnectionSharing"), this document is much newer.

Firestater is no longer recommended, as it isn't supported any more. Ufw is installed by default, and if you need a gui, install gufw.

---

### Post by dracule on 2009-09-27
thanks it is working now.

---

