---
title: "installed the AR81Family-linux-v1.0.1.6.tar.gz driver"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by wstay on 2010-03-14
I installed the AR81Family-linux-v1.0.1.6.tar.gz driver for my new motherboard, model Gigabyte S-series G31M-ES2L on my ubuntu 8.10 system with the following errors:
wstay@wstay-ubuntu8:~$ ls
Desktop  Documents  Examples  Music  Pictures  Public  Templates  Videos
wstay@wstay-ubuntu8:~$ cd Desktop/
wstay@wstay-ubuntu8:~/Desktop$ ls
AR81Family-linux-v1.0.1.6.tar.gz  ubuntu8.10-menu.lst
wstay@wstay-ubuntu8:~/Desktop$  tar zxvf AR81Family-linux-v1.0.1.6.tar.gz 
atl1e.7
atl1e.spec
at_osdep.h
copying
dkms.conf
ldistrib.txt
Makefile
pci.updates
readme
release_note.txt
src/
src/atl1c.h
src/atl1c_ethtool.c
src/atl1c_hw.c
src/atl1c_hw.h
src/atl1c_main.c
src/atl1c_param.c
src/atl1e.h
src/atl1e_ethtool.c
src/atl1e_hw.c
src/atl1e_hw.h
src/atl1e_main.c
src/atl1e_param.c
src/at_common.h
src/at_common_main.c
src/at_osdep.h
src/kcompat.c
src/kcompat.h

gzip: stdin: decompression OK, trailing garbage ignored
src/kcompat_ethtool.c
src/Makefile
src/Module.markers
src/Module.symvers
src/modules.order
tar: Child returned status 2
tar: Error exit delayed from previous errors
wstay@wstay-ubuntu8:~/Desktop$ cd src/
wstay@wstay-ubuntu8:~/Desktop/src$ sudo apt-get install linux-headers-generic build-essential make
[sudo] password for wstay: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
make is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages
wstay@wstay-ubuntu8:~/Desktop/src$ 

Can someone please help me solve this problem?

---

### Post by sohelmk on 2010-06-24
Hi,

I am facing lots of issues with getting wireless/AR9285 working on Dell  Vostro 1014 with ath9k. I have posted all details here:

[http://ubuntuforums.org/showthread.php?t=1516415](http://ubuntuforums.org/showthread.php?t=1516415)

Can you please advise if you were able to use this driver from atheros  and if i should try the same?

Thanks a lot,
Sohel.

---

