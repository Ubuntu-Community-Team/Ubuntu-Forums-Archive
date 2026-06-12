---
title: "&quot;Linuxant&quot; &amp; Debian 6 problem!"
date: 2011-03-15
forum: Multimedia Software
---

### Post by quisnox on 2011-03-15
Hello! I have strange problem with sound in my Debian 6 machine, when trying to install Linuxant driver.


 I've got error:


 ```
root@bbspqn-k52f:/home/qn/Desktop# dpkg -i alsa-driver-linuxant_1.0.23.1_all.deb
Selecting previously deselected package alsa-driver-linuxant.
(Reading database … 310249 files and directories currently installed.)
Unpacking alsa-driver-linuxant (from alsa-driver-linuxant_1.0.23.1_all.deb) …
Setting up alsa-driver-linuxant (1.0.23.1) …
Building modules for the 2.6.32-5-686-bigmem kernel, please wait… done.
ERROR: Build failed. Please review the build log at /tmp/alsa-driver-linuxant.3210.log
dpkg: error processing alsa-driver-linuxant (–install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 alsa-driver-linuxant
```


 Then, I’ve checked log file, and looks like problem is:




```
ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run ‘make oldconfig && make prepare’ on kernel src to fix it.
   WARNING: Symbol version dump /usr/src/linux-headers-2.6.32-5-common/Module.symvers
           is missing; modules will have no dependencies and modversions.
 find: `/usr/src/linux-headers-2.6.32-5-common/alsa-kernel/’: No such file or directory
find: `/usr/src/linux-headers-2.6.32-5-common/alsa-kernel/’: No such file or directory
find: `/usr/src/linux-headers-2.6.32-5-common/alsa-kernel/’: No such file or directory
  Building modules, stage 2.
/usr/src/linux-headers-2.6.32-5-common/scripts/Makefile.modpost:42: include/config/auto.conf: No such file or directory
find: `/usr/src/linux-headers-2.6.32-5-common/alsa-kernel/’: No such file or directory
find: `/usr/src/linux-headers-2.6.32-5-common/alsa-kernel/’: No such file or directory
find: `/usr/src/linux-headers-2.6.32-5-common/alsa-kernel/’: No such file or directory
make[2]: *** No rule to make target `include/config/auto.conf’.  Stop.
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-5-common’
make: *** [compile] Error 2

```I’ve tried to do make oldconfig && make prepare in kernel source, but got another error:


 ```
scripts/Makefile.build:44: /usr/src/linux-headers-2.6.32-5-common/scripts/basic/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-headers-2.6.32-5-common/scripts/basic/Makefile’.  Stop.
make: *** [scripts_basic] Error 2
```
 What can I do? I have Alsa and kernel sources installed both

[I][FONT=Courier New][SIZE=1]
[/SIZE][/FONT][/I]
[COLOR=Silver]*[FONT=Courier New][SIZE=1]and sorry for my poor English...[/SIZE][/FONT]*[/COLOR]

---

### Post by www.rzr.online.fr on 2011-10-13
some track or dead end :
[http://lists.debian.org/debian-user/2009/07/msg00639.html](http://lists.debian.org/debian-user/2009/07/msg00639.html)


-- 
[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)

---

