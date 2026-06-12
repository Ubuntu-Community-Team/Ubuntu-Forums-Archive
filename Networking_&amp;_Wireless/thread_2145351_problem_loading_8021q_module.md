---
title: "problem loading 8021q module"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by bishalpun on 2013-05-15
Hello All,

 I have installed 12.04 server for pppoe server with 2 nice cards. I am trying to implement VLAN on eth1 and did install the vlan with apt-get install vlan. Everything went fine until I load 8021q module. I got the following errors while loading 8021q module
root@pppoe-01:~# modprobe 8021q
FATAL: Module 8021q not found.

root@pppoe-01:~# locate 8021q.ko
/lib/modules/3.2.0-29-generic-pae/kernel/net/8021q/8021q.ko
/lib/modules/3.2.0-31-generic-pae/kernel/net/8021q/8021q.ko


root@pppoe-01:~# uname -a
Linux pppoe-01 3.2.17 #2 SMP Wed May 15 13:02:02 NPT 2013 i686 i686 i386 GNU/Linux


Any help?

thank you
Bishal

---

