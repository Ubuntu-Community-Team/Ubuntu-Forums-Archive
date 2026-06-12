---
title: "ipw2200-ap on Breezy Bagder: make problems"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by flostre on 2006-05-10
Hi,

I'm running Breezy Badger on my laptop and I'd like it to behave as a wlan access point. The ipw2200 drivers are doing fine, but I just can't compile ipw2200-ap.

When I do make, it goes:

```

make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/flostre/iub/ipw2200-ap-0.2 MODVERDIR=/home/flostre/iub/ipw2200-ap-0.2 modules
make: *** /lib/modules/2.6.12-10-386/build: File or directory not found. Stopping.
make: *** [modules] Error 2

```

Has anybody had the same problem? Or can somebody report on their success running ipw2200-ap?

Thanks in advance,
flostre

---

### Post by drejom on 2007-04-04
Did you have any luck with this? 
I'm trying to do the same with my laptop. I made it a bit further by installing the kernel headers, but now get this error when trying to make:

```
make -C /lib/modules/2.6.20-13-386/build SUBDIRS=/home/denis/Desktop/ipw2200-ap-
0.3 MODVERDIR=/home/denis/Desktop/ipw2200-ap-0.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-13-386'
rm: cannot remove `/home/denis/Desktop/ipw2200-ap-0.3/net': Is a directory
make[1]: *** [crmodverdir] Error 1
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-13-386'
make: *** [modules] Error 2
```

and am left with an empty directory other than the 'net' dir.
Any help appreciated....

---

### Post by xchip on 2007-07-29
I'm in the same situation....  did you figure out how to compile it?

Thanks!

---

### Post by steigleitung on 2007-08-09
I, too, am unable to compile this. Does anybody know?

---

### Post by medomedo on 2007-11-26
Here the same problem. I think the problem is not driver specific but rather old vs. new kernel structure. I am saying this because I have the same problem while trying to compile rt8081 driver (wireless PCMCIA).

Any Idea/hint is appreciated.

---

### Post by f0ku5 on 2008-03-26
Bump. I am having the same problem.

---

