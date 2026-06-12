---
title: "Mobile Media Converter"
date: 2009-03-15
forum: Multimedia Software
---

### Post by jaijaiyro on 2009-03-15
hey guys im having trouble trying to install this App
but i tryed several things so far can some one tell me whats the right way to do this 

```
jae@jay-laptop:~$ dpkg --force-architecture -i ./mmc_1.4.1_i386.deb
dpkg: requested operation requires superuser privilege
jae@jay-laptop:~$ sudo dpkg --force-architecture -i ./mmc_1.4.1_i386.deb
[sudo] password for jae: 
dpkg: error processing ./mmc_1.4.1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ./mmc_1.4.1_i386.deb
jae@jay-laptop:~$ sudo apt-get install dpkg --force-architecture -i ./mmc_1.4.1_i386.deb
E: Command line option --force-architecture is not understood
jae@jay-laptop:~$ 
```

---

### Post by Mr_bleu on 2009-03-15
Try:
jae@jay-laptop:~$ dpkg -i --force-architecture  mmc_1.4.1_i386.deb

---

### Post by Mr_bleu on 2009-03-15
I can't edit posts for some reason, it times out.
jae@jay-laptop:~$ sudo dpkg -i --force-architecture mmc_1.4.1_i386.deb

---

