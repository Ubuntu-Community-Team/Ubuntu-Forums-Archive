---
title: "Line6 soundcard doesn't work after driver install"
date: 2010-12-27
forum: Multimedia Software
---

### Post by jerry85 on 2010-12-27
I've been trying to install the linux driver for line6 devices.
here are a few links:
[http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)
[http://www.tanzband-scream.at/line6/INSTALL](http://www.tanzband-scream.at/line6/INSTALL)

when following the install instructions I get a lot of errors. and I'm not sure the installation is successful for there is no new soundcard available in the soundsettings menu.

any ideas?
thanks!! 

first I installed RPMbuild:

```
jeroen@jeroen-Ubuntu:~$ rpmbuild -tb /home/jeroen/Downloads/line6usb-0.8.1.tar.bz2
The program 'rpmbuild' is currently not installed.  You can install it by typing:
sudo apt-get install rpm
jeroen@jeroen-Ubuntu:~$ sudo apt-bet install rpm
[sudo] password for jeroen: 
sudo: apt-bet: command not found
jeroen@jeroen-Ubuntu:~$ sudo apt-get install rpm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  librpm1 librpmbuild1 librpmio1 rpm-common rpm2cpio
Suggested packages:
  alien elfutils rpm-i18n
The following NEW packages will be installed:
  librpm1 librpmbuild1 librpmio1 rpm rpm-common rpm2cpio
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,661kB of archives.
After this operation, 5,816kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://be.archive.ubuntu.com/ubuntu/ maverick/main librpmio1 i386 4.8.1-5 [770kB]
Get:2 http://be.archive.ubuntu.com/ubuntu/ maverick/main rpm-common i386 4.8.1-5 [714kB]
Get:3 http://be.archive.ubuntu.com/ubuntu/ maverick/main librpm1 i386 4.8.1-5 [876kB]
Get:4 http://be.archive.ubuntu.com/ubuntu/ maverick/main librpmbuild1 i386 4.8.1-5 [761kB]
Get:5 http://be.archive.ubuntu.com/ubuntu/ maverick/main rpm2cpio i386 4.8.1-5 [699kB]
Get:6 http://be.archive.ubuntu.com/ubuntu/ maverick/main rpm i386 4.8.1-5 [839kB]
Fetched 4,661kB in 4s (1,032kB/s)
Selecting previously deselected package librpmio1.
(Reading database ... 143092 files and directories currently installed.)
Unpacking librpmio1 (from .../librpmio1_4.8.1-5_i386.deb) ...
Selecting previously deselected package rpm-common.
Unpacking rpm-common (from .../rpm-common_4.8.1-5_i386.deb) ...
Selecting previously deselected package librpm1.
Unpacking librpm1 (from .../librpm1_4.8.1-5_i386.deb) ...
Selecting previously deselected package librpmbuild1.
Unpacking librpmbuild1 (from .../librpmbuild1_4.8.1-5_i386.deb) ...
Selecting previously deselected package rpm2cpio.
Unpacking rpm2cpio (from .../rpm2cpio_4.8.1-5_i386.deb) ...
Selecting previously deselected package rpm.
Unpacking rpm (from .../archives/rpm_4.8.1-5_i386.deb) ...
Processing triggers for man-db ...
Setting up librpmio1 (4.8.1-5) ...
Setting up rpm-common (4.8.1-5) ...
Setting up librpm1 (4.8.1-5) ...
Setting up librpmbuild1 (4.8.1-5) ...
Setting up rpm2cpio (4.8.1-5) ...
Setting up rpm (4.8.1-5) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```then I tried the rpmbuild instruction which was unsuccessful, followed by a source installation :
```
jeroen@jeroen-Ubuntu:~$ rpmbuild -tb /home/jeroen/Downloads/line6usb-0.8.1.tar.bz2
error: Failed build dependencies:
    kernel-source is needed by line6usb-0.8.1-1.i386
jeroen@jeroen-Ubuntu:~$ cd /home/jeroen/Downloads/line6usb-0.8.1
jeroen@jeroen-Ubuntu:~/Downloads/line6usb-0.8.1$ make install
./set_revision.sh
make -f Makefile -C /lib/modules/2.6.35-22-generic/build CONFIG_LINE6_USB=m SUBDIRS=/home/jeroen/Downloads/line6usb-0.8.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/jeroen/Downloads/line6usb-0.8.1/audio.o
/home/jeroen/Downloads/line6usb-0.8.1/audio.c: In function ‘line6_init_audio’:
/home/jeroen/Downloads/line6usb-0.8.1/audio.c:31: error: implicit declaration of function ‘snd_card_new’
/home/jeroen/Downloads/line6usb-0.8.1/audio.c:31: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/jeroen/Downloads/line6usb-0.8.1/audio.o] Error 1
make[1]: *** [_module_/home/jeroen/Downloads/line6usb-0.8.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [default] Error 2
jeroen@jeroen-Ubuntu:~/Downloads/line6usb-0.8.1$ modprobe line6usb
FATAL: Error inserting line6usb (/lib/modules/2.6.35-22-generic/kernel/drivers/staging/line6/line6usb.ko): Operation not permitted

```afterwards tried some things, also unsuccessful..

```
jeroen@jeroen-Ubuntu:~/Downloads/line6usb-0.8.1$ cd ..
jeroen@jeroen-Ubuntu:~/Downloads$ rpmbuild -tb line6usb-0.8.1.tar.bz2
error: Failed build dependencies:
    kernel-source is needed by line6usb-0.8.1-1.i386
jeroen@jeroen-Ubuntu:~/Downloads$ rpmbuild -tb reamping-0.1-1.i586.rpm.del
error: Failed to read spec file from reamping-0.1-1.i586.rpm.del
jeroen@jeroen-Ubuntu:~/Downloads$ rpm -U reamping-0.1-1.i586.rpm.del
rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
    /bin/sh is needed by reamping-0.1-1.i586
    libasound.so.2 is needed by reamping-0.1-1.i586
    libasound.so.2(ALSA_0.9) is needed by reamping-0.1-1.i586
    libasound.so.2(ALSA_0.9.0rc4) is needed by reamping-0.1-1.i586
    libc.so.6 is needed by reamping-0.1-1.i586
    libc.so.6(GLIBC_2.0) is needed by reamping-0.1-1.i586
    libc.so.6(GLIBC_2.1.3) is needed by reamping-0.1-1.i586
    libgcc_s.so.1 is needed by reamping-0.1-1.i586
    libgcc_s.so.1(GCC_3.0) is needed by reamping-0.1-1.i586
    libgcc_s.so.1(GLIBC_2.0) is needed by reamping-0.1-1.i586
    libm.so.6 is needed by reamping-0.1-1.i586
    libsndfile.so.1 is needed by reamping-0.1-1.i586
    libsndfile.so.1(libsndfile.so.1.0) is needed by reamping-0.1-1.i586
    libstdc++.so.5 is needed by reamping-0.1-1.i586
    libstdc++.so.5(CXXABI_1.2) is needed by reamping-0.1-1.i586
    libstdc++.so.5(GLIBCPP_3.2) is needed by reamping-0.1-1.i586
    libsysfs.so.1 is needed by reamping-0.1-1.i586
jeroen@jeroen-Ubuntu:~/Downloads$ sudo apt-get install Alien
[sudo] password for jeroen: 
Sorry, try again.
[sudo] password for jeroen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Alien

```

---

### Post by dino99 on 2010-12-27
sudo apt-get install line6-usb-source

[http://packages.ubuntu.com/source/maverick/line6-usb](http://packages.ubuntu.com/source/maverick/line6-usb)

---

### Post by jerry85 on 2010-12-27
Ubuntu just keeps surprising me...
installed it with software center :)

thanks!

---

### Post by jerry85 on 2010-12-29
I installed It, it just didn't do nothing, there still is no line6 soundcard displayed in the soundsettings.
what could be the problem? I did find some info on launchpad: [https://bugs.launchpad.net/ubuntu/+source/line6-usb/+bug/401969](https://bugs.launchpad.net/ubuntu/+source/line6-usb/+bug/401969)
but this didn't seem to help..

---

### Post by jerry85 on 2010-12-29
hi there! I have a line6 pod studio GX and tried to install the tanzband driver using the ubuntu software center but nothing happened.
there is still no line6 soundcard in my soundoptions menu. 
I googled and searched the forum for a while but couldn't find a solution..

can anyone help me?

thanks!

here is some alsa project info:
[http://www.alsa-project.org/db/?f=b10967dfeaecc005ec29971ef4e1ecda4f0d60c3](http://www.alsa-project.org/db/?f=b10967dfeaecc005ec29971ef4e1ecda4f0d60c3)

---

### Post by jerry85 on 2010-12-31
I've been trying to get my Line 6 POD studio gx to work but no luck so far. I've installed the driver using the software center, but the soundcard doesn't show up in the sound settings menu..
I'm not shure what the problem is, there is very little info on the subject.

---

### Post by Iowan on 2010-12-31
Merged 3 threads.
If you'd prefer to have the thread in Multimedia & Video, use the "Report abuse" button to request a move.

From Code of Conduct:
> # Do not cross post, or post the same thing in multiple locations.

---

### Post by Elfy on 2011-01-02
moved bumped

---

