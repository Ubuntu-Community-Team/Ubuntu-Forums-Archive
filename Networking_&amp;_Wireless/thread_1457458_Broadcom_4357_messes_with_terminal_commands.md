---
title: "Broadcom 4357 messes with terminal commands"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by whaler1 on 2010-04-18
Just put 9.10 on a HP dv6-2150 with a Broadcom 4357 wireless controller.  Installed the bcmwl-kernel-source package to get the supposed proper driver.  When I activate the driver the wireless works fine but my file/directory structure appears to get lost and I cannot use the terminal to change directories/open files etc.  The following is what happens;

ie.
steve@Ubuntu:~$ sudo -s gedit '/etc/bash.bashrc' 
bash: sudo -s gedit /etc/bash.bashrc: No such file or directory

or
steve@Ubuntu:~$ cd '/media' 
bash: cd /media: No such file or directory
 
If I deactivate the driver the terminal commands work fine again but unfortunately then I don't have wireless.  I am interested to know if anyone else has come across this problem or can suggest a fix.  
 
Many thanks,

---

### Post by AggravatedGestalt on 2011-03-31
This piece of proprietary crap also gives me problems with terminal commands, markedly, ifconfig & iwconfig commands. I hope they release the source. For now, it is yet another menacing broadcom chip.

---

