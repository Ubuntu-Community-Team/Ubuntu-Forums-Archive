---
title: "another 3945 question [error message]"
date: 2006-07-04
forum: Networking &amp; Wireless
---

### Post by jaden403 on 2006-07-04
Ubuntu 6.06
Kernel 2.6.15-25-386
Dell Inspiron 9400

I have searched through this forum but cannot find this specific problem addressed.

I downloaded the Intel driver from sourceforge.com as well as the other files listed there.  What does this error mean?

#make

Checking in /lib/modules/2.6.15-25-386 for ieee80211 components...
find: /lib/modules/2.6.15-25-386/build/: No such file or directory
grep: /lib/modules/2.6.15-25-386/build//.config: No such file or directory
grep: /lib/modules/2.6.15-25-386/build//include/linux/autoconf.h: No such file or directory
find: /lib/modules/2.6.15-25-386/build/: No such file or directory
make -C /lib/modules/2.6.15-25-386/build M=/home/joshua/Desktop/ieee80211-1.1.14 modules
make: *** /lib/modules/2.6.15-25-386/build: No such file or directory.  Stop.
make: *** [modules] Error 2

Thanks...

---

