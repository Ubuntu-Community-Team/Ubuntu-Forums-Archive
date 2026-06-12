---
title: "log for sockets"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by anonmars on 2009-08-13
Which log would contain messages about the system running out of sockets? Ie. if a program were not closing sockets appropriately

---

### Post by Brandon Williams on 2009-08-15
There would usually be a problem with the application having too many file descriptors open before there would be a system-level problem, unless you have used ulimit to increase the number of fds allowed for the program to some gigantic number. Look in the log for the program that's having trouble to figure out whether any system calls are failing due to too many open files.

---

