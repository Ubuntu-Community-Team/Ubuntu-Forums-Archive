---
title: "error 2 no such file or directory when running sudo make"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by bradw on 2009-11-02
Here is the error message Im getting when running both the sudo make command and also sudo make install. Can someone tell me what Im doing wrong?

root@ubuntuserver:~/test/2009_0918_RT2860_Linux_STA_v2.2.0.0# sudo make
make -C tools
make[1]: Entering directory `/home/brad/test/2009_0918_RT2860_Linux_STA_v2.2.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/brad/test/2009_0918_RT2860_Linux_STA_v2.2.0.0/tools'
/home/brad/test/2009_0918_RT2860_Linux_STA_v2.2.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/brad/test/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.24-25-server/build SUBDIRS=/home/brad/test/2009_0918_RT2860_Linux_STA_v2.2.0.0/os/linux modules
make: *** /lib/modules/2.6.24-25-server/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
root@ubuntuserver:~/test/2009_0918_RT2860_Linux_STA_v2.2.0.0#

I think it has something to do with this in the make file but Im not sure

ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
CROSS_COMPILE = 
endif

---

### Post by hal10000 on 2009-11-02
The directory /lib/modules/2.6.24-25-server/build, which is a symbolic link to  /usr/src/linux-headers-2.6.24-25-server (or to (usr/src/linux i guess, if you have the kernel sources installed) does'nt exist on your system
I guess you have to install the kernel-headers or the linux kernel-source package.

---

### Post by bradw on 2009-11-02
> **hal10000 said:**
> The directory /lib/modules/2.6.24-25-server/build, which is a symbolic link to  /usr/src/linux-headers-2.6.24-25-server (or to (usr/src/linux i guess, if you have the kernel sources installed) does'nt exist on your system
I guess you have to install the kernel-headers or the linux kernel-source package.

Both of those are loaded per synaptic. Im new to linux and dont have a clue what Im doing. Im trying to follow the directions in the readme file that came with the download from ralink. chipset is 2860. Im running commands from my home folder if that makes a difference as that is where the directory is.

thanks

Brad

---

### Post by hal10000 on 2009-11-02
Are you trying to compile/install wireless drivers? 
Did you first try do get them working with the precompiled driver? In linux the most drivers are already installed by default or you can install them with your package manager. In the most cases you don't need to compile them yourself.
Maybe you should first open a thread about the problems you have to get your wireless working or search for other threads related to your problem.

---

