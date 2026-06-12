---
title: "cannot install ndiswrapper"
date: 2006-06-29
forum: Networking &amp; Wireless
---

### Post by hojotoolee2 on 2006-06-29
Hi all,
I tried to install ndiswrapper, but it is giving me something like this:

Can't find kernel build files in /lib/modules/2.6.15-25-386/build;
  give the path to kernel build directory with
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/me/Desktop/ndiswrapper-1.18/driver'
make: *** [all] Error 2

how do i go around resolving this problem???

---

### Post by marmux on 2006-07-07
you have to install the headers for your kernel. Find out your kernel version with
```
uname -r
```
and install the appropriate linux-headers-$your-version$ with synaptic. This solved the problem for me

---

