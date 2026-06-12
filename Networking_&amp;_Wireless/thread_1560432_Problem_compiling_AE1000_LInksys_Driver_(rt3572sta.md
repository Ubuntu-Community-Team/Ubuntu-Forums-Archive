---
title: "Problem compiling AE1000 LInksys Driver (rt3572sta)"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by harvero on 2010-08-24
I'm trying to compile the AE1000 Linksys Wireless driver per the instructions found on "http://forums.fedoraforum.org/showthread.php?p=1353558" from ralink. 

I"ve made the changes to the driver source and am trying to compile it but get the following error:

////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
harvero@ubuntu:~/wireless/2010_0709_RT3572_Linux_STA_v2.4.0.1$ make
make -C tools
make[1]: Entering directory `/home/harvero/wireless/2010_0709_RT3572_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/harvero/wireless/2010_0709_RT3572_Linux_STA_v2.4.0.1/tools'
/home/harvero/wireless/2010_0709_RT3572_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/harvero/wireless/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.24-28-server/build SUBDIRS=/home/harvero/wireless/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux modules
make: *** /lib/modules/2.6.24-28-server/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

If I add a "build" directory under /lib/modules/2.6.24-28-server/, then the error is:
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
make[1]: Entering directory `/lib/modules/2.6.24-28-server/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.24-28-server/build'
make: *** [LINUX] Error 2
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

I'm a little new to Ubuntu/Linux - any help is much appreciated.

Thanks

---

### Post by crovian on 2011-08-11
you need to get the linux-headers

sudo apt-get install linux-headers

---

