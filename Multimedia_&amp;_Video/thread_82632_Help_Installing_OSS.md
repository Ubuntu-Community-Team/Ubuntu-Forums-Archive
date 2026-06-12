---
title: "Help Installing OSS"
date: 2005-10-26
forum: Multimedia &amp; Video
---

### Post by jrc on 2005-10-26
I'm trying to install OSS so I can have sound, but I keep running into problems.  The messages I get from the OSS soundconf.log are meaningless to me.  I was told by the OSS help person that I need to install the kernel souce, but that didn't seem to help.  If anyone is up to the challenge of deciphering the soundconf.log and telling me what I need to do, here it is:  

Wed Oct 26 19:34:44 EDT 2005
Kernel version: Linux dhcppc0aland 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
Modutils version: 3.2-pre7
 19:34:44 up 25 min,  2 users,  load average: 0.21, 0.23, 0.19
=== Running ./bin/soundconf ===
Install directory: /usr/lib/oss
Will use /usr/bin/ld for linking.
Will use /usr/bin/ld for linking.
grep: /lib/modules/2.6.12-9-386/build/Makefile: No such file or directory
ln: `/lib/modules/2.6.12-9-386/source': File exists
Note: No /lib/modules/2.6.12-9-386/source/.config installed
./kbuild.sh: line 43: cd: /lib/modules/2.6.12-9-386/source/include: No such file or directory
Try `uname --help' for more information.
make -C /lib/modules/`uname -r`/source scripts scripts_basic include/linux/version.h
make: *** /lib/modules/2.6.12-9-386/source: No such file or directory.  Stop.
make: [ossbuild] Error 2 (ignored)
make -C /lib/modules/`uname -r`/source SUBDIRS=/usr/lib/oss/kbuild CC="gcc" modules
make: *** /lib/modules/2.6.12-9-386/source: No such file or directory.  Stop.
make: *** [ossbuild] Error 2
Kbuild didn't work....using bruteforce method
/lib/modules/2.6.12-9-386/build/include/linux/version.h does not exist
/usr/src/linux-2.6.12-9-386/include/linux/version.h does not exist

**** Failed to compile the sndshield module ****


Cannot find the kernel include directory. Make sure you have the kernel
sources installed.
Set the KERNELINCLUDE variable and try again if you have the kernel
sources in a nonstandard place.
No sndshield module available.
OSS/Linux kernel module not available. Cannot continue.

---

