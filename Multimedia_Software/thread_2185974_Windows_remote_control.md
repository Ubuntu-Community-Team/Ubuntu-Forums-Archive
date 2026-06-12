---
title: "Windows remote control"
date: 2013-11-05
forum: Multimedia Software
---

### Post by deanie44 on 2013-11-05
Hi everyone.  I have a Windows remote control(Rc6) that I have been using for two months with Mythbuntu 12.04.3 and it has worked in the frontend of Mythtv.  Unfortunately it does not work anymore.  How do I get it to work again?  I have read many articles and posts, but do not understand the jargon.  I did not upgrade the kernal or Mythtv.  Any assistance will be helpful. deanie44:(

Update:  I tried to fixed the problem in a terminal, but I did not work:

sweetie55@sweetie55:~$  sudo dpkg-reconfigure lirc 
[sudo] password for sweetie55: 
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
ls: cannot access /lib/modules/3.8.0-32-generic/kernel/drivers/staging/lirc: No such file or directory
 * Loading LIRC modules                                                  [ OK ] 
 * Unable to load LIRC kernel modules. Verify your
 * selected kernel modules in /etc/lirc/hardware.conf
sweetie55@sweetie55:~$

---

