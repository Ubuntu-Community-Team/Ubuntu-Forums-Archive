---
title: "Trying to get ati driver 10.9 to work"
date: 2010-10-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by anku on 2010-10-03
I having problems to get this to run but got errors installing it



anku@anku-desktop:~$ cd ~/Desktop
anku@anku-desktop:~/Desktop$ chmod +x '/home/anku/Desktop/ati-driver-installer-10-9-x86.x86_64.run' 
anku@anku-desktop:~/Desktop$ sudo '/home/anku/Desktop/ati-driver-installer-10-9-x86.x86_64.run' 
[sudo] password for anku: 
Created directory fglrx-install.4bJKLB
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.771.............................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.4bJKLB
anku@anku-desktop:~/Desktop$

---

### Post by Claus7 on 2010-10-03
Hello,

check this out:
[http://ubuntuforums.org/showthread.php?t=1221221](http://ubuntuforums.org/showthread.php?t=1221221)

Regards!

---

### Post by ktp on 2010-10-03
why not just install the fglrx drivers in repository, which already support latest xorg?

---

### Post by jfernyhough on 2010-10-03
Exactly.

$ sudo apt-get install fglrx
$ sudo aticonfig --initial

Reboot.

---

### Post by anku on 2010-10-03
because Im trying to get a game to work sc2 and I heard that installing the ati driver from to site works better to get the problems that im having with it

---

### Post by cariboo on 2010-10-03
You better check version numbers, as the driver in the repo's is only 1½ to 2 weeks old. You're probably trying to install the same driver the hard way.

---

### Post by jfernyhough on 2010-10-03
The repository version is newer than 10.9; it's basically a 10.10 pre-release. Expect 10.10 to be driver version 8.780. The relationship with ATi is one of the advantages Ubuntu has over some of the other distros.

---

### Post by tanari on 2010-10-05
if I install fglrx from repos I get white screen after restart...

---

### Post by Claus7 on 2010-10-05
Hello,

first get rid of anything that has to do with graphics drivers. Then with sudo apt-get fglrx* install the necessary proprietary packages for ati drivers while on command line mode via recovery mode.

Then restart. See what you get. If bad screens are the result, try sudo aticonfig -initial, taking care before that no xorg.conf file exists under /etc/X11. Also check out if the driver has been enabled.

If both cases do not work, remove once again everything about fglrx and try the link I have provided you before to install the proprietary drivers now from ati's website and not from ubuntu repos.

In between check if the type of your graphics card is supported by the proprietary driver, cause if not, this won't help you, and you have to stick with the open ones. Just a guide on what I would do if I were in your shoes.

Regards!

---

