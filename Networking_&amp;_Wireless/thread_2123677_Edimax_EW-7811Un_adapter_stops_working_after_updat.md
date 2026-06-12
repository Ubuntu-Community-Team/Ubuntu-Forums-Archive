---
title: "Edimax EW-7811Un adapter stops working after update to 3.7.0-7-generic kernel"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by falcofire on 2013-03-08
Hello,

I followed instructions to correctly set up the adapter for initial use using Realtek's latest driver. Worked great. Got lots of updates done and almost had system like I wanted it. Then did an update to latest kernel (I am running 32bit 12.10) and on reboot, adapter began exhibiting the signs of seeing networks but not connecting. I followed the steps to install Realtek's driver again but am unable to get the module to load. I get:

FATAL: Error inserting 8192cu (/lib/modules/3.7.0-7-generic/kernel/drivers/net/wireless/8192cu.ko): Unknown symbo in module, or unknown parameter (see dmesg)

Any suggestions? 

Also I have no access to wired internet on that box. I have a laptop that I'm currently using but until I resolve this issue I can't download new headers or anything on that box.

---

### Post by mikewhatever on 2013-03-08
Doesn't look like you've blacklisted the original built in module. You should do that, by adding **blacklist rtl8192cu** to /etc/modprobe.d/blaclist.conf. Reboot, then try rebuilding.

PS: 12.10 shouldn't have the 3.7 kernel in the repositories. You might want to stick to the tried and tested 3.5.

---

### Post by falcofire on 2013-03-08
I have definitely blacklisted the orginial rtl8192cu module. How do I remove the 3.7 kernel repositories and keep it on 3.5?

---

### Post by mikewhatever on 2013-03-09
That error usually happens when any of the associated modules are incompatible with the one that has been built. If the original module has been blacklisted, then, perhaps, you've tried installing compa-wireless. 

How did you install the 3.7 kernel? Have you added any repositories?

---

### Post by ahallubuntu on 2013-03-09
~

---

