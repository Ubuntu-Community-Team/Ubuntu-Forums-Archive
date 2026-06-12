---
title: "Nvidia drivers"
date: 2008-02-15
forum: Multimedia &amp; Video
---

### Post by Tsmizzit on 2008-02-15
Hi all, I'm getting the green fuzzy screen thing on divx and after some research found that the latest nvidia driver would stop this. However, once downloaded i can't install it. When i type the line "sh NVIDIA-Linux-x86_64-169.07-pkg2.run"  into terminal it says something like access denied, and this is on my admin account.

Any help appreciated,

Tom

---

### Post by jan quark on 2008-02-15
and this ?

```
sudo sh NVIDIA-Linux-x86_64-169.07-pkg2.run
```

---

### Post by Tsmizzit on 2008-02-15
no sorry i get this message: 'sh: Can't open NVIDIA-Linux-x86_64-169.07-pkg2.run'

---

### Post by PmDematagoda on 2008-02-15
Were you in the directory containing the file when you executed that command?

---

### Post by pbcartwright on 2008-02-15
first, I believe the filename is:
NVIDIA-Linux-x86-169.09-pkg1.run
pkg1.run NOT pkg2..

and 2nd you need to NOT have xwindows running, it won't work.
so you need to reboot into single user mode OR go to the command line text login ( CTRL-ALT-F1)
and do :
/etc/init.d/kdm stop

then cd to the folder where your NVIDI *.run file is, THEN issue the command:
sh NVIDIA-Linux-x86-169.09-pkg1.run

---

### Post by banished_one on 2008-02-15
or you can use ENVY

---

### Post by StrangeBrew on 2008-02-15
How can you download that file from rescue mode?

---

