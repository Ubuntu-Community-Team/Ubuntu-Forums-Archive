---
title: "tcpdump user privilage"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by kaltsi on 2011-08-23
Hi, 

Why can't tcpdump open this file?

kaltsi@snoopy:~$ tcpdump -r /home/snoop/201108230929.dmp
tcpdump: /home/snoop/201108230929.dmp: Permission denied


kaltsi@snoopy:~$ ls -l /home/snoop/201108230929.dmp
-rw-r--r-- 1 snoop snoop 364517328 2011-08-23 10:35 /home/snoop/201108230929.dmp

---

