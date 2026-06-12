---
title: "Ubuntu 11.10 Intel 4965AGN aireplay -1 channel problem patch"
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by Fernandbteich on 2012-08-14
Hello
I'm running Ubuntu 11.10 and my wireless card is an intel 4965 AGN.
When I try to use aireplay I get the wrong channel (-1) error.
I tried to patch it using the guide in this thread: [http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)
When I reach the "make" step, I get the following error:

root@ubuntu:/home/user/compat-wireless-2010-10-16# make
make: Makefile: No such file or directory
make: *** No rule to make target `Makefile'.  Stop.
[: 1: -gt: argument expected
test: 1: -ge: unexpected operator
make -C /lib/modules/3.0.0-23-generic/build M=/home/user/compat-wireless-2010-10-16 modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-23-generic'
make[1]: Makefile: No such file or directory
make[1]: *** No rule to make target `Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-23-generic'
make: *** [modules] Error 2

Please help. I don't know how to solve this.
linux-headers-3.0.0-23-generic_3.0.0-23.39_i386.deb is installed.
Any help is appreciated.

---

