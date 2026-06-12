---
title: "Another HomePNA problem"
date: 2005-12-27
forum: Networking &amp; Wireless
---

### Post by escifell on 2005-12-27
I have just installed the latest version of Ubuntu (Breezy) on my home PC. I use homePNA networking and it works under an old version of Fedora (2). My network card uses the AMD 79c978 chip and uses the pcnet32 driver. I note that there is a difference between the two versions of the driver the Fedora code defaults to PNA mode whereas the newer Ubuntu code defaults to Ethernet (patch by Simmons 2004). To fix the card to switch to PNA appears to be simple - set the option

options pcnet32 homepna=1

I have tried every-which way. Adding the line to /etc/modprobe.d/aliases, creating the option line in a file in modprobe.d called pcnet32, and/or in /etc/modutils. I have depmod/modprobed and module-updated but to no avail. On boot the card always goes into ethernet mode.

What I am doing wrong, or how can I insert an older version of the driver pre-simmons patch?

Thanks for any advice.

---

### Post by Lambert on 2005-12-29
see if this helps you.

[http://forums.linuxiso.org/viewtopic.php?t=25439&sid=b0ad30f66bfec28a4383847761d49f76](http://forums.linuxiso.org/viewtopic.php?t=25439&sid=b0ad30f66bfec28a4383847761d49f76)

---

### Post by escifell on 2006-01-03
OK that helped and it is now working. The issue is that the module pcnet32 is either built as part of the kernel in the default distro or it is loaded very early in the boot process so when it executes /etc/init.d/module-init-tools modprobe cannot update the options and effectively does nothing. The solution was to add a line in module-init-tools before the main loop to read:

modprobe -r pcnet32

then in /etc/modules insert the line

pcnet32 homepna=1

It now correctly boots every time!

---

