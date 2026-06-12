---
title: "Setting ASUS NX1101 card at 1000mb"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by bob1949 on 2011-06-15
Hi,

I've installed Ubuntu 11.04 on an IBM Thinkcentre PC it's all is going well but I wanted to upgrade the network card to support 1gbit to match the rest of my network.

I installed a ASUS NX1101 card but it's only showing support for 10 or 100 mbit

The box included a disc of drivers including one for folder for linux (v2.09e)

I've tried to compile it as per the read.me but I get this error
================================================
bob@ibm1:~/Downloads/Linux_v2.09e$ make all
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/bob/Downloads/Linux_v2.09e modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'  
    CC [M]  /home/bob/Downloads/Linux_v2.09e/ipg_main.o
In file included from /home/bob/Downloads/Linux_v2.09e/ipg_main.c:159:0:
/home/bob/Downloads/Linux_v2.09e/ipg.h:101:26: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[2]: *** [/home/bob/Downloads/Linux_v2.09e/ipg_main.o] Error 1
make[1]: *** [_module_/home/bob/Downloads/Linux_v2.09e] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [all] Error 2
bob@ibm1:~/Downloads/Linux_v2.09e$ 

============================================
Can anyone help me resolve the compile error ?
OR is there some way to select an existing driver that supports 1gbit

Has any been able to get this card working at 1gbit

Regards,

Bob

---

### Post by joshhanna on 2011-07-25
I am facing the same problem and would love to resolve the issue.

-josh

---

### Post by bob1949 on 2011-07-25
Josh,

Sorry but I never resolved it - I also discovered that when the PC woke from "sleep" it lost the network connection and I could not get it back withpu a reboot.

The Ubuntu project was a test to see if I could replace Win XP on a PC that I use as a media centre / EPG uploader  - it sits under my TV in the lounge room. 

In the end I gave up and bought a 3X licence pack for WIN7 after install it immediatley configured the ASUS card to support 1000mb and I there are no problems seeing the network when it wakes.

Sorry I couldn't help

(Note WIN7 is not perfect either I still have one problem there but at least it's doing the job)

BobS

---

### Post by joshhanna on 2011-07-25
I am currently running a dual boot Win 7 Ubuntu Server. I think that Ubuntu would be more powerful as it requires less to run. I put this network card in just so I could run Gigabit. The on board NIC works and is fine just sucks for transferring large files.

-josh

p.s. The NX1101 only cost me $10. so I'm not that sad by not being able to configure it.

---

### Post by joshhanna on 2011-07-25
Did you ever try to contact Asus support for help?

-josh

---

