---
title: "tcp and wireless network"
date: 2005-12-26
forum: Networking &amp; Wireless
---

### Post by xstation on 2005-12-26
I am thinking of installing postfix.

my tcp ports on network look like this

Is it possible to set up a postfix server on these ports


y108@heis:~$ sudo netstat --extend -e
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode
tcp        0      0 localhost.localdoma:ipp localhost.localdo:38480 ESTABLISHEDcupsys     10994
tcp        0      0 localhost.localdo:32769 localhost.localdo:33261 ESTABLISHEDhplip      9658
tcp        0      0 localhost.localdo:33261 localhost.localdo:32769 ESTABLISHEDhplip      9743
tcp        0      0 localhost.localdo:38480 localho

---

