---
title: "Unable to compile RaLink Wireless Drivers for Kernel 3.2.0-26"
date: 2012-07-02
forum: Networking &amp; Wireless
---

### Post by JoeNixx on 2012-07-02
Hello There !

I've just ran the updates suggested by the Ubuntu Upgrade Manager (12.04), Since it was a Generic Kernel upgrade (to version 3.2.0-26) I already knew I had to recompile my wireless driver once the upgrade was done in order to have Wireless functionality once again, No big deal... The following commands suggested by the Awesome **chili555** usually do the trick:

```
sudo su
  cd /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
make clean
make
make install
  modprobe rt3562sta
exit
```

Except this time around, I got the following errors while issuing **make**

```
root@jarvis:/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217# make
make -C tools
make[1]: Entering directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools'
/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/tools/bin2h
cp -f os/linux/Makefile.6 /home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/Makefile
make -C /lib/modules/3.2.0-26-generic-pae/build SUBDIRS=/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux modules
make: *** /lib/modules/3.2.0-26-generic-pae/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
root@jarvis:/home/jose/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217#
```

Could someone please help me with this error, I sincerely have no idea about what's going on.

Thanks in advance!

Best Regards

---

### Post by chili555 on 2012-07-02
Please check that you have the linux-header package installed:```
sudo apt-get install linux-headers-generic-pae
```Then recompile. Thanks.

---

### Post by JoeNixx on 2012-07-02
Hi there chili5555 ! Good to see you !

Here's are the results of your suggested command...

```
jose@jarvis:~$ sudo apt-get install linux-headers-generic-pae
[sudo] password for jose: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunity6 libdee-1.0-1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-26-generic-pae
The following NEW packages will be installed:
  linux-headers-3.2.0-26-generic-pae
The following packages will be upgraded:
  linux-headers-generic-pae
1 upgraded, 1 newly installed, 0 to remove and 27 not upgraded.
Need to get 981 kB of archives.
After this operation, 11.2 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com/ubuntu/ precise-security/main linux-headers-3.2.0-26-generic-pae i386 3.2.0-26.41
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ precise-security/main linux-headers-generic-pae i386 3.2.0.26.28
  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-26-generic-pae_3.2.0-26.41_i386.deb  Could not resolve 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic-pae_3.2.0.26.28_i386.deb  Could not resolve 'security.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

It looks as if it tried to reach the internet to fix some stuff, but since I don't have access now, I believe It couldn't make it, right?

Thank you as always. 
Let me know what you think.

PS. Recompilation prompted the same error.. :(

---

### Post by JoeNixx on 2012-07-02
Hello again, and especially to **chili55**,

Fortunately, I figured out a way of installing the headers which I wasn't able to install due to lack of internet connection.

I downloaded the following packages (and placed them on my computer using a stick):

```
http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-26_3.2.0-26.41_all.deb
http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.2.0-26-generic-pae_3.2.0-26.41_i386.deb
```

And then I installed them via sudo dpkg -i

After that compilation worked smoothly (as it usually does)

I hope this is useful to someone else facing the same problem. As usual chili555, you're my hero, only your cape is missing.

Thanks a bunch!

---

### Post by chili555 on 2012-07-02
It will be very helpful, now that you have internet access, to go ahead and install the generic piece as above.

Glad it's working.

---

