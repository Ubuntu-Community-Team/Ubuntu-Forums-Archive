---
title: "Has gufw been removed from the repositories?"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by MoebusNet on 2009-11-18
glenn@glenn-laptop:~$ sudo apt-get install gufw ufw
[sudo] password for glenn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gufw

Ubuntu 8.04.3

---

### Post by dmizer on 2009-11-18
GUFW has never been available for Hardy via the repos. However, you can download the Hardy deb from Launchpad: [https://launchpad.net/gui-ufw/+download](https://launchpad.net/gui-ufw/+download)

---

### Post by MoebusNet on 2009-11-18
Thank you! :)

---

### Post by MoebusNet on 2009-11-18
Hmmmm... I guess I was a little premature marking this thread as solved; I know that gufw isn't in the repositories for Hardy but Launchpad doesn't seem to have it either (it's marked obsolete).

I may have to look for an alternative to ufw. Suggestions for a firewall with a GUI will be welcomed.

---

### Post by MoebusNet on 2009-11-18
[SOLVED] (again) I finally managed to track down gufw at:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

which just redirected to a Launchpad link:

[http://launchpad.net/gui-ufw/gufw-8.04-8.10/8.04-8.10/+download/gufw_0.20.7-all.deb](http://launchpad.net/gui-ufw/gufw-8.04-8.10/8.04-8.10/+download/gufw_0.20.7-all.deb)

I guess Launchpad was doing something that prevented me from downloading before (shrugs).

Anyway, so far so good for ufw & gufw!

---

