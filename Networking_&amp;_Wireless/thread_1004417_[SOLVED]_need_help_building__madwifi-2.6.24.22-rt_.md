---
title: "[SOLVED] need help building  madwifi-2.6.24.22-rt kernel"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by rixtr66 on 2008-12-07
could someone help me with building madwifi with the 2.6.24.22-rt kernel.
I tried building with the kernelpath /usr/src/linux,but its not there,
only the headers are there.so where are the kernel sources for ubuntu 8.04.1? I have Build-essential installed so thats not a problem.
what do i do now?currently im running ndis wrapper.but i want to get away from using windows drivers.any help would be appreciated!!!!
Peace
Rick

---

### Post by rixtr66 on 2008-12-07
I managed to figure it out!!i down loaded the kernel sources,then got the latest release of madwifi through svn.ran make,sudo make install,restarted.
set wicd to ath0 and bingo it worked!\\:D/
yaaaaaay!!
Peace
Rick
):P

---

