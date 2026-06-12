---
title: "Issues installing WUSB600N Driver"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by Dog Man on 2010-08-29
I have absolutely no experience with Linux and I am sure that will be obvious.

I am trying to get my Linksys USB wireless adapter installed.  I have followed the **How To** article that was posted on this site and had the following errors: when issuing the MAKE command.

I have no idea what the heck I am doing and hope that some one can tell me what went wrong.  I have double checked all the previous steps.  

ken@ken-desktop:~/WUSB600N$ sudo make
make -C tools
make[1]: Entering directory `/home/ken/WUSB600N/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/ken/WUSB600N/tools'
/home/ken/WUSB600N/tools/bin2h
cp -f os/linux/Makefile.6 /home/ken/WUSB600N/os/linux/Makefile
make  -C  /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/ken/WUSB600N/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/ken/WUSB600N/os/linux/../../common/rtmp_init.o
  CC [M]  /home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.o
/home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/ken/WUSB600N/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/ken/WUSB600N/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [LINUX] Error 2
ken@ken-desktop:~/WUSB600N$

---

### Post by MaindotC on 2010-08-29
It appears that the Makefile has instructions to look for a file in a location that doesn't exist or is incorrect.  You may not even have the header files it's looking for.  Do you have /usr/src/linux-headers-2.6.32-24-generic?  Can you check the readme file to see if it specifies what kernel version and dependies you require for this driver to be compiled properly?

---

