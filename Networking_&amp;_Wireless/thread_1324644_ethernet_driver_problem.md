---
title: "ethernet driver problem"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by DReeves922 on 2009-11-12
I was installing Ubuntu 9.04 on a Dell Vostro 200 and got some problems.
Ethernet would not connect, turns out I needed driver e10007.6.5, which I dled off the dell site.
went through the commands:
```
#tar xfvz e1000-7.6.5.tar.gz
#cd e1000-7.6.5/src/
#sudo make install
```I then get this error:
```
#make -C /lib/modules/2.6.28-11-generic/build SUBDIRS=/home/reeves/e1000-7.6.5/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/username/e1000-7.6.5/src/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/username/e1000-7.6.5/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
```Can anyone help me out?

---

### Post by DReeves922 on 2009-11-12
Anyone at all?
Found someone who suggested changing all the CFLAGS to EXTRA_CFLAGS in the makefile... sounds like it's almost to simple to be true.  ](*,)

---

### Post by DReeves922 on 2009-11-12
Meh, nevermind. 4 hours of looking an can't seem to find any working fix.
Back to XP it goes :|

---

