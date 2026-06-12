---
title: "k9copy crashes at launch time on Gnome"
date: 2009-05-06
forum: Multimedia Software
---

### Post by goaliefight on 2009-05-06
This is a clean install of 9.04. k9copy opened once and crashed after about 30 seconds. Since then, it wont load at all.

$ uname -a
Linux e6400 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux


$ k9copy 
KCrash: Application 'k9copy' crashing...
sock_file=/home/nick/.kde/socket-e6400/kdeinit4__0
Warning: connect() failed: : No such file or directory
KCrash cannot reach kdeinit, launching directly.

Application: k9copy (k9copy), signal SIGSEGV
0x00007f5d58e318f5 in waitpid () from /lib/libc.so.6

Thread 1 (Thread 0x7f5d5d51a750 (LWP 6998)):
[KCrash Handler]
#4  0x000000000042a863 in _start ()


Thanks in advance for any support.

---

### Post by goaliefight on 2009-05-08
Update - I filed a bug report

[https://bugs.launchpad.net/bugs/373793](https://bugs.launchpad.net/bugs/373793)

---

### Post by running_rabbit07 on 2010-01-13
Well, that is a KDE program. That might be the problem.

---

