---
title: "Wireless in earlier kernel but not later one!"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by benon on 2009-05-09
I have two kernels on my ubuntu hardy. The earlier kernel's wireless works just fine. The later one which i installed from updates has no wireless. Tried to search the forums for a HOW TO or something but nothing.

benon@benon-laptop:~$ sudo lshw
[sudo] password for benon: 
benon-laptop              
    description: Portable Computer
    product: Vostro A860
    vendor: Dell Inc.
benon@benon-laptop:~$ lsb_release -d
Description:	Ubuntu 8.04.2

benon@benon-laptop:~$ uname -mr
2.6.24-19-generic i686
**This is the earlier kernel that accesses wireless.**

The newer one that doesn't access wireless is 2.6.24-23-generic i686
Any suggestions appreciated.

---

### Post by RedSingularity on 2009-05-09
What is your "lspci" output?

---

