---
title: "Sharing TrueCrypt NTFS drive over NFS"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by Doktor-X on 2012-07-18
hi boys and girls i'm having problem setting up trucrypt nfs sharing to use i't on my openelec raspberrypi.

i have dualboot win 8 and ubuntu 12.04 using wubi, on windows i can make  nfs share to work using haneWIN and i can watch xvid movies but mkv dts  stutter so i wanted to see if maybe native nfs support wood be better so i  deside to try nfs using 12.04 ubuntu installed over wubi

so trucrypt mount drive in standard /media/truecrypt1 location and all files are ok localy
so i edit /etc/exports and put inside ```
 /media/truecrypt1 *(rw,no_root_squash)
```
after that i restart nfs service and use command showmount -e and i see that i't ok

but on openelec i can only get to /media/truecrypt1 location nothig beyond that

---

