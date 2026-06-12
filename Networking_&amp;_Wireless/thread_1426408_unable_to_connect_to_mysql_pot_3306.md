---
title: "unable to connect to mysql pot 3306"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by savin on 2010-03-10
Error Details:
Could not connect to host '204.232.204.88'.
MySQL Error Nr. 1045
Access denied for user 'root'@'122.169.182.34' (using password: YES)


netstat-details:

netstat -p 3306
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 slice134316:ssh         ABTS-AP-dynamic-0:35273 ESTABLISHED 11617/sshd: xx
tcp        0      0 slice134316:mysql       ABTS-AP-dynamic-0:46609 TIME_WAIT   -               
tcp        0      0 slice134316:mysql       ABTS-AP-dynamic-0:46605 TIME_WAIT   -               
Active UNIX domain sockets (w/o servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ]         DGRAM                    7438     1801/udevd          @/org/kernel/udev/udevd
unix  4      [ ]         DGRAM                    10133    2169/rsyslogd       /dev/log
unix  2      [ ]         DGRAM                    98159    11978/logger        
unix  3      [ ]         STREAM     CONNECTED     97579    11617/sshd: xx
unix  3      [ ]         STREAM     CONNECTED     97578    11623/0             
unix  2      [ ]         DGRAM                    97430    11587/jsvc          
unix  3      [ ]         DGRAM                    7441     1801/udevd          
unix  3      [ ]         DGRAM                    7440     1801/udevd          
unix  3      [ ]         STREAM     CONNECTED     7424     1/init              @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     7423     1799/upstart-udev-b 


system details:
uname (GNU coreutils) 7.4
Copyright (C) 2009 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by David MacKenzie.



uname -a       
Linux slice134316 2.6.31-302-rs #7 SMP Thu Oct 29 22:57:03 UTC 2009 x86_64 GNU/Linux


lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.10
Release:    9.10
Codename:    karmic




help me on tis error

---

