---
title: "[SOLVED] You already have noloader configuration"
date: 2008-07-16
forum: Mythbuntu
---

### Post by GuiGuy on 2008-07-16
A google on this gave me no help. The Mythbuntu box did an update overnight. Now  the update program is stuck on 

"You already have noloader configuration in /etc/grub.conf
Running boot loader as requested
Running /usr/sbin/grub  ... "

I forced a reboot and tried to do a recovery on the packages. No luck.The reboot is stuck on the above message.  I wouldn't know where to begin troubleshooting.

Any practical help, anyone?

TIA

---

### Post by GuiGuy on 2008-09-12
> **GuiGuy said:**
> A google on this gave me no help. The Mythbuntu box did an update overnight. Now  the update program is stuck on 

"You already have noloader configuration in /etc/grub.conf
Running boot loader as requested
Running /usr/sbin/grub  ... "

I forced a reboot and tried to do a recovery on the packages. No luck.The reboot is stuck on the above message.  I wouldn't know where to begin troubleshooting.



For the benefit of anyone else who might be struck down by this, 

> 
sudo rm /etc/grub.conf
sudo apt-get update
sudo apt-get install


should fix it

---

