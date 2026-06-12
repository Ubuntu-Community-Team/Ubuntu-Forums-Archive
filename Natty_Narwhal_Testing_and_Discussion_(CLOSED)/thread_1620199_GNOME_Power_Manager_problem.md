---
title: "GNOME Power Manager problem"
date: 2010-11-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rubenverweij on 2010-11-12
Hi all!
I booted my pc after some updates and I got this error:
```
The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator.
```
So I tried the obvious solutions posted on the web:
```

sudo dpkg-reconfigure -a
sudo dpkg --configure -a
sudo chmod 077 /tmp
sudo mkdir /var/lib/gconf/default
sudo aptitude reinstall ubuntu-desktop
sudo aptitude reinstall gnome-power-manager

```
But the problem persists. So I delved in the log files:
```
[   41.823916] gconfd-2[1041]: segfault at 706d7433 ip 00320817 sp bffa676c error 4 in libc-2.12.1.so[2b3000+157000]
[   41.862364] gconfd-2[1043]: segfault at 706d7433 ip 002be817 sp bfddefcc error 4 in libc-2.12.1.so[251000+157000]
[   41.898311] gconfd-2[1045]: segfault at 706d7433 ip 00461817 sp bf8d78dc error 4 in libc-2.12.1.so[3f4000+157000]
```
These are the first three, but it was repeated more often.
Is anyone else seeing this? Could it be connected with my power manager warning?
Should I submit a bug report?
Cheers,
Ruben

---

### Post by cariboo on 2010-11-12
Yes you should submit a bug report, make sure to use ubuntu-bug, so that as much info as possible gets included.

---

