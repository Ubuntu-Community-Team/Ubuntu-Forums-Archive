---
title: "Trying to install NIC Drivers for new Motherboard (RTL8168D Gigibit)"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by mikel3757 on 2009-01-17
Hello...  I'm a newbe trying to install a RealTek Linux Driver for a new motherboard I'm testing (RTL8168-8).  I have downloaded the tarball, copied it to a Tmp directory in my Desktop workspace, opened the tarball, and created the install directory, that all worked fine.

I did a the following (from the README):

user@user-desktop:~/Tmp$ ls
r8168-8.010.00  r8168-8.010.00.tar.bz2
user@user-desktop:~/Tmp$ lsmod | grep r8169
r8169                  33156  0 

and then...

user@user-desktop:~/Tmp/r8168-8.010.00$ sudo rmmod r8169
user@user-desktop:~/Tmp/r8168-8.010.00$

user@user-desktop:~/Tmp$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done

All fine sofar...

Then attempted to do "make clean modules", with the following...

user@user-desktop:~/Tmp/r8168-8.010.00$ sudo make clean modules
make -C src/ clean
make[1]: Entering directory `/home/user/Tmp/r8168-8.010.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/home/user/Tmp/r8168-8.010.00/src'
make -C src/ modules
make[1]: Entering directory `/home/user/Tmp/r8168-8.010.00/src'
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/user/Tmp/r8168-8.010.00/src'
make: *** [modules] Error 2

I assumed I had missed an install step, so I checked the apt-get install build-essential...

user@user-desktop:~/Tmp/r8168-8.010.00$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 8711kB of archives.
After this operation, 34.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-23.46 [703kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libc6-dev 2.7-10ubuntu4 [3344kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libstdc++6-4.2-dev 4.2.4-1ubuntu3 [1187kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++-4.2 4.2.4-1ubuntu3 [2784kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main patch 2.5.9-4 [95.6kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7066B]
Fetched 8711kB in 4s (1905kB/s)   
Selecting previously deselected package linux-libc-dev.
(Reading database ... 113637 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-23.46_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu4_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.4-1ubuntu3_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.24-23.46) ...
Setting up libc6-dev (2.7-10ubuntu4) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up libstdc++6-4.2-dev (4.2.4-1ubuntu3) ...
Setting up g++-4.2 (4.2.4-1ubuntu3) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...

This followed by:

user@user-desktop:~/Tmp/r8168-8.010.00$ make
make -C src/ clean
make[1]: Entering directory `/home/user/Tmp/r8168-8.010.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/home/user/Tmp/r8168-8.010.00/src'
make -C src/ modules
make[1]: Entering directory `/home/user/Tmp/r8168-8.010.00/src'
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/home/user/Tmp/r8168-8.010.00/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /home/user/Tmp/r8168-8.010.00/src/r8168_n.o
/home/user/Tmp/r8168-8.010.00/src/r8168_n.c: In function ‘rtl8168_hw_phy_config’:
/home/user/Tmp/r8168-8.010.00/src/r8168_n.c:1398: warning: unused variable ‘data’
/home/user/Tmp/r8168-8.010.00/src/r8168_n.c: In function ‘rtl8168_down’:
/home/user/Tmp/r8168-8.010.00/src/r8168_n.c:4838: warning: unused variable ‘poll_locked’
/home/user/Tmp/r8168-8.010.00/src/r8168_n.c: At top level:
/home/user/Tmp/r8168-8.010.00/src/r8168_n.c:2675: warning: ‘rtl8168_phy_power_down’ defined but not used
include/asm/io_32.h: In function ‘memcpy_fromio’:
include/asm/io_32.h:211: warning: passing argument 2 of ‘__memcpy’ discards qualifiers from pointer target type
  LD [M]  /home/user/Tmp/r8168-8.010.00/src/r8168.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/user/Tmp/r8168-8.010.00/src/r8168.mod.o
  LD [M]  /home/user/Tmp/r8168-8.010.00/src/r8168.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
strip --strip-debug r8168.ko
make[1]: Leaving directory `/home/user/Tmp/r8168-8.010.00/src'
make -C src/ install
make[1]: Entering directory `/home/user/Tmp/r8168-8.010.00/src'
install -m 744 -c r8168.ko /lib/modules/2.6.24-23-generic/kernel/drivers/net/
install: cannot create regular file `/lib/modules/2.6.24-23-generic/kernel/drivers/net/r8168.ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/user/Tmp/r8168-8.010.00/src'
make: *** [install] Error 2

I assumed I had incorrect permissions, so I repeated under sudo....

user@user-desktop:~/Tmp/r8168-8.010.00$ sudo make
make -C src/ clean
make[1]: Entering directory `/home/user/Tmp/r8168-8.010.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers *.order
make[1]: Leaving directory `/home/user/Tmp/r8168-8.010.00/src'
make -C src/ modules
make[1]: Entering directory `/home/user/Tmp/r8168-8.010.00/src'
make -C /lib/modules/2.6.24-23-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
scripts/Makefile.build:41: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/user/Tmp/r8168-8.010.00/src'
make: *** [modules] Error 2

Suggestions????

---

### Post by mikel3757 on 2009-01-17
Update...

I got the driver to compile by copying the tar files to /src....

I also had to manually copy the driver (r8168.ko) to /lib/modules/2.6.24-23-generic/kernel/drivers/net

If I do a "insmod r8168.ko" then eth0 comes up fine....

I then did a "sudo depmod -aeq"  I'm rebooting now.

That reboot worked fine.....

---

