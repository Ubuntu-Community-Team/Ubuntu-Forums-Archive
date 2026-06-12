---
title: "Frustrated with fglrx"
date: 2010-07-25
forum: Multimedia Software
---

### Post by ludwigvan1988 on 2010-07-25
I have an ATI Radeon X300 video card and I've been trying to set up dual monitors. A few people have said this is possible if I install a fglrx driver and edit xorg.conf. I, however, can't seem to get fglrx to work.

$ fglrxinfo 
Segmentation fault

$ dmesg | fglrx
[  115.424294] fglrxinfo[1699]: segfault at 4 ip 00007fe83509812e sp 00007fff286dec90 error 4 in libGL.so.1.2[7fe835042000+a2000]
[  443.134289] fglrxinfo[1742]: segfault at 4 ip 00007f4e7865e12e sp 00007fff96656800 error 4 in libGL.so.1.2[7f4e78608000+a2000]
[ 1255.459043] fglrxinfo[1836]: segfault at 4 ip 00007f714bc5c12e sp 00007fff319ea520 error 4 in libGL.so.1.2[7f714bc06000+a2000]
[ 2148.517595] fglrxinfo[1937]: segfault at 4 ip 00007ff01b9d512e sp 00007fff056d6f70 error 4 in libGL.so.1.2[7ff01b97f000+a2000]

does anyone recognize these messages?

---

### Post by Yellow Pasque on 2010-07-25
WHat version of Ubuntu are you using? If it's >= 9.04, fglrx doesn't support your card. Uninstall it and reinstall the open-source driver: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

### Post by ludwigvan1988 on 2010-07-26
Ubuntu 10.04 is installed

---

