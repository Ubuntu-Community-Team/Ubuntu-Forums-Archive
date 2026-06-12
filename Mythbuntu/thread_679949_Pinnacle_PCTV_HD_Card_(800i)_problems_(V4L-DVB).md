---
title: "Pinnacle PCTV HD Card (800i) problems (V4L-DVB)"
date: 2008-01-27
forum: Mythbuntu
---

### Post by dreadh3ad on 2008-01-27
Hey everyone,

While i have some experience with ubuntu I am still a relative noob with linux.
I am attempting to follow the installation directions at: [http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29](http://www.linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Card_%28800i%29) on the newest version of mythbuntu.

I have extracted the firmware but problems arise with the V4L-DVB module.  I followed the installation instructions as per [http://linuxtv.org/repo/](http://linuxtv.org/repo/)

However i run into problems when i attempt to make:

bakamyth@bakamyth-desktop:~/v4l-dvb$ make
make -C /home/bakamyth/v4l-dvb/v4l 
make[1]: Entering directory `/home/bakamyth/v4l-dvb/v4l'
Updating/Creating .config
Preparing to compile for kernel version 2.6.22
File not found: /lib/modules/2.6.22-14-generic/build/.config at ./scripts/make_kconfig.pl line 32, <IN> line 4.
make[1]: *** No rule to make target `.myconfig', needed by `config-compat.h'.  Stop.
make[1]: Leaving directory `/home/bakamyth/v4l-dvb/v4l'
make: *** [all] Error 2

What went wrong?

---

### Post by pops66 on 2008-02-04
It almost looks like you may not have all the kernel headers installed. Look for and install something along the lines of linux-headers-generic.  If that doesn't work for you, post back with a little more detail about your setup (version of Ubuntu, kernel version, version of gcc, etc...)

Also, how did you get v4l-dvb?  Mercurial?  If not you should have.

---

