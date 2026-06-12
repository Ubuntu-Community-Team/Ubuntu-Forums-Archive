---
title: "Cisco VPN client not finding kernel sources"
date: 2006-06-24
forum: Networking &amp; Wireless
---

### Post by LiquidStranger on 2006-06-24
Hi everyone!
I'm trying to install the Cisco VPN Client which i need to connect to the wireless network at university but i keep running into some problems:
The installer ask me for some paths, including the one to the kernel-sources. As i didn't know at first, where to find those i checked the paths it recommended and (presumably) found them at /usr/src/:
```
marc@ubuntop:/usr/src$ ls
kernel-build-2.4.27-2           kernel-headers-2.4.27-2-686-smp
kernel-headers-2.4.27-2         kernel-headers-2.4.27-2-k6
kernel-headers-2.4.27-2-386     kernel-headers-2.4.27-2-k7
kernel-headers-2.4.27-2-586tsc  kernel-headers-2.4.27-2-k7-smp
kernel-headers-2.4.27-2-686     kernel-source-2.4.27.tar.bz2

```
But none of these folders work, i always get the following error:
```
* Kernel source from "/usr/src/kernel-headers-2.4.27-2" will be used to build the module.

Is the above correct [y]

Making module
make -C /usr/src/kernel-headers-2.4.27-2 SUBDIRS=/home/marc/1_downloads/vpnclient modules
make[1]: Entering directory `/usr/src/kernel-headers-2.4.27-2'
gcc-3.3 -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -o scripts/split-include scripts/split-include.c
scripts/split-include.c:22:23: sys/types.h: No such file or directory
scripts/split-include.c:23:22: sys/stat.h: No such file or directory
scripts/split-include.c:25:19: ctype.h: No such file or directory
scripts/split-include.c:26:19: errno.h: No such file or directory
scripts/split-include.c:27:19: fcntl.h: No such file or directory
scripts/split-include.c:28:19: stdio.h: No such file or directory
scripts/split-include.c:29:20: stdlib.h: No such file or directory
scripts/split-include.c:30:20: string.h: No such file or directory
scripts/split-include.c:31:20: unistd.h: No such file or directory
scripts/split-include.c: In function `main':
scripts/split-include.c:50: error: `FILE' undeclared (first use in this function)
scripts/split-include.c:50: error: (Each undeclared identifier is reported only once
scripts/split-include.c:50: error: for each function it appears in.)
scripts/split-include.c:50: error: `fp_config' undeclared (first use in this function)
scripts/split-include.c:51: error: `fp_target' undeclared (first use in this function)
scripts/split-include.c:52: error: `fp_find' undeclared (first use in this function)
scripts/split-include.c:61: error: storage size of `stat_buf' isn't known
scripts/split-include.c:66: warning: implicit declaration of function `fprintf'
scripts/split-include.c:66: error: `stderr' undeclared (first use in this function)
scripts/split-include.c:67: warning: implicit declaration of function `exit'
scripts/split-include.c:75: warning: implicit declaration of function `stat'
scripts/split-include.c:76: error: `errno' undeclared (first use in this function)
scripts/split-include.c:76: warning: implicit declaration of function `perror'
scripts/split-include.c:80: warning: implicit declaration of function `malloc'
scripts/split-include.c:80: warning: assignment makes pointer from integer without a cast
scripts/split-include.c:81: error: `NULL' undeclared (first use in this function)
scripts/split-include.c:81: warning: assignment makes pointer from integer without a cast
scripts/split-include.c:82: warning: assignment makes pointer from integer without a cast
scripts/split-include.c:86: warning: implicit declaration of function `fopen'
scripts/split-include.c:92: warning: implicit declaration of function `mkdir'
scripts/split-include.c:97: warning: implicit declaration of function `chdir'
scripts/split-include.c:105: warning: implicit declaration of function `fgets'
scripts/split-include.c:113: warning: implicit declaration of function `strstr'
scripts/split-include.c:118: warning: implicit declaration of function `isspace'scripts/split-include.c:121: warning: implicit declaration of function `isupper'scripts/split-include.c:121: warning: implicit declaration of function `tolower'scripts/split-include.c:134: warning: implicit declaration of function `fclose'
scripts/split-include.c:136: warning: implicit declaration of function `strcmp'
scripts/split-include.c:159: warning: implicit declaration of function `fputs'
scripts/split-include.c:160: warning: implicit declaration of function `ferror'
scripts/split-include.c:191: warning: implicit declaration of function `popen'
scripts/split-include.c:205: warning: implicit declaration of function `strlen'
scripts/split-include.c:222: warning: implicit declaration of function `pclose'
scripts/split-include.c:61: warning: unused variable `stat_buf'
make[1]: *** [scripts/split-include] Fehler 1
make[1]: Leaving directory `/usr/src/kernel-headers-2.4.27-2'
make: *** [default] Fehler 2
Failed to make module "cisco_ipsec.ko".

```
So i ran a "uname -r" and found i was using kernel "2.6.15-25-386" which is different from the sources i have. But using "apt-get install kernel-source-2.6.15-25" resulted in a packet not found error.
Any suggestions what i'm doing wrong?

---

### Post by DoughRayMe on 2006-06-24
Use apt-get install linux-source-2.6.15 to get the sources

This link might be useful as well.

[http://ubuntuforums.org/archive/index.php/t-21054.html](http://ubuntuforums.org/archive/index.php/t-21054.html)

---

### Post by LiquidStranger on 2006-06-24
Okay, now i've got the vpnclient installed but it won't connect due to missing or incorrect information in the profile. Gotta ask my university admins for the details, i guess.
Tanks a lot for your help, that got me a lot closer to dumping XP from my laptop :)

---

