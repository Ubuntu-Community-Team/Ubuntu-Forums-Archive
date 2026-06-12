---
title: "wireless chipset &amp; 9.04"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by drudogg on 2009-07-14
i am tired of fighting the stupid wireless card on my laptop. and fed up with spending hours on commandline stuff that doesn't work like it should. running ubuntu 9.04

so i have been through 3 mpci cards and i want to get another that will just work. i do not mind a quick thing to make it happen, not opposed to ndiswrapper or wicd. just don't want to have to fight with it.

suggestions on what chipset to look for in a mpci card for laptop?? not intel...

---

### Post by drudogg on 2009-07-15
solved... i have a broadcom 4306 mpci card. it works with the instructions on this link:

[http://www.linuxwireless.org/en/users/Drivers/b43?action=show&redirect=en/users/Drivers/bcm43xx#devicefirmware](http://www.linuxwireless.org/en/users/Drivers/b43?action=show&redirect=en/users/Drivers/bcm43xx#devicefirmware)

---

### Post by gutierrezfam on 2009-07-16
I've followed the instructions in the link you posted.  Everything went well.  What's the next step, though?  Do we have to tell system to use the new driver (via ndiswrapper) or something?  Thanks.

---

### Post by drudogg on 2009-07-16
it just started working for me after a restart... not sure it just kind of leaves you hanging doesn't it?  mine is working, but is slow. still troubleshooting. hoping i do not have to go back to winblows...

---

