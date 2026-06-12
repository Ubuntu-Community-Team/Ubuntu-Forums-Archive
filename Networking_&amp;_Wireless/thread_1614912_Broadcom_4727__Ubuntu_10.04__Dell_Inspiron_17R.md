---
title: "Broadcom 4727 / Ubuntu 10.04 / Dell Inspiron 17R"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by bengateau on 2010-11-06
Hi all,

I have brand new Dell Inspiron 17R (came with no preinstalled OS) and having problems getting wifi connection to work. I read posts here and this is what I have:

'lspci' does not list 'Wireless Brand', I get:
Network controller: Broadcom Corporation Device 4727 (rev 01)
Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)

running 'iwconfig' displays:
lo       no wireless extensions.
pan0   no wireless extensions. 

'lsmod' is not displaying anything starting with 'wlan'

running 'sudo lshw -C network' is showing both of them as '*-network UNCLAIMED' which I understand means I need to install drivers, but because ethernet is also unclaimed, I cannot simply plug wired cable and run update and install the required drivers.

I have tried to install 'bcmwl-kernel-source' as suggested in one of the posts, even though my Broadcom is version 4727 and 'bcmwl-kernel-source' supports 4311, 4312, 4321 and 4322. Trying to install it from CD I got error:
/usr/sbin/dkms: line 35: patch: command not found
Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+dcdom/buld/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-isntallation script returned error exit status 6
 
Even though it failed it appeared as if it was installed, and it was visible under System/Administration/Hardware Drivers. But when trying to Active, I got "SystemError: installArchives() failed"
 
I have also tried to install Ubuntu 10.10, but at the very beginning I was getting error "GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)"

What an utter crap this Dell experience has been so far ... Anyway, if someone can suggest what I can do to get it working, I'd love to hear it.

Cheers, Ben

---

### Post by chili555 on 2010-11-06
> patch: command not foundCan you install the package *patch* from the CD and then try again?

---

### Post by bengateau on 2010-11-06
Thank you chili555, that was it. Happy days :D

Cheers, Ben

ps. How can I mark this thread as Closed?

---

### Post by chili555 on 2010-11-06
Glad it's working.> How can I mark this thread as Closed?I believe at the top, under Thread Tools, you have the option to "Mark as Solved." I am not totally sure because I never started a thread; and therefor never was solved.

Have fun with Ubuntu!

---

