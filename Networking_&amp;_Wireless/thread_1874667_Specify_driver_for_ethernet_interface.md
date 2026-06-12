---
title: "Specify driver for ethernet interface"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by henningels on 2011-11-03
How do I tell Ubuntu to use a specific driver for an interface?
 
I have 2 network cards installed and both are using e1000e.  I replaced one with a 10G Intel 82599EB card which requires a different driver, ixgbe.  I now want to tell Ubuntu to use ixgbe driver for those interface (eth2&3).  
 
I got the system to load both e1000e and ixgbe (shows up with lsmod) but when I do ethtool -i eth2, it still shows e1000e.
 
uname -a
Linux 2.6.31-20-server #58-Ubuntu SMP Fri.. x86_64 GNU/Linux
 
Thanks in advance.

---

