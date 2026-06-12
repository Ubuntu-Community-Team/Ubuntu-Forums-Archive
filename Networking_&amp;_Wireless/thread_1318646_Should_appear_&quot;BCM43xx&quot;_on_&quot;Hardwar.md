---
title: "Should appear &quot;BCM43xx&quot; on &quot;Hardware Drivers&quot;?"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by another_sam on 2009-11-07
Today I installed Ubuntu 9.10 on a machine with a BCM43xx wifi chip. I realized that no references to this card are given at "System" > "Administration" > "Hardware Drivers", nor the possibility of installing b43-fwcutter package from there.

How is it supposed that users should know they have to, and how to, install this driver? Only by reading [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) / [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) ? Or should Ubuntu provide a more pro-active and assisted method?

Obviously I think that if there is no such method, it would be convenient to create it.

---

### Post by snowpine on 2009-11-07
Hi Sam, I hope this is not a stupid question :) but is your wireless functional or not? Many Broadcom cards are supported by the kernel out-of-the-box with no restricted driver necessary.

---

### Post by another_sam on 2009-11-08
Hi. nono, that's a good question. 

the machine is a laptop Compaq Presario R3000 . it is not mine and I have not access to that machine anymore. but, maybe someone could talk us about his own experience.

what happened yesterday:
1. at the beginning wifi did not work. 
2. then I installed ndiswrapper without understanding well what I was doing. - after reboot, wifi did not work.
3. then I installed b43-fwcutter through apt-get
4. after reboot, wifi worked; wifi led on, several networks discovered, and successful connection to one of them.
5. then I disabled wireless through network-manager-gnome
6. then I enabled again wireless through network-manager-gnome, but then it wasn't able to re-find the wireless networks. even using iwlist scan.
7. then I uninstalled b43-fwcutter through apt-get. rebooted, and then it worked again.

so, it is hard to understand for me what happened.

---

