---
title: "Easy Steps to Upgrade ALSA 1.0.19"
date: 2009-05-06
forum: Multimedia Software
---

### Post by kondetisree on 2009-05-06
**_What is Alsa (Advanced Linux Sound Architecture) ?_** According to [Wikipedia]("http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture"), Alsa is a Linux kernel component intended to replace the original Open Sound System (OSS) for providing device drivers for sound cards. Some of the goals of the ALSA project at its inception were automatic configuration of sound-card hardware, and graceful handling of multiple sound devices in a system, goals which it has largely met.
 **_Installation :_**
 To do this, we must begin by determining our version of alsa as follows :

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
 [LEFT]We must then install the necessary tools to compile along with the kernel headers :[/LEFT]
 sudo apt-get -y install build-essential ncurses-dev gettext xmlto
sudo apt-get -y install linux-headers-`uname -r`
 Then, we go in our personal folder and download alsa-driver, alsa-lib and alsa-utils :
 cd ~
wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.19.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.19.tar.bz2)
wget [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.19.tar.bz2)
 After that, we create a new folder for the compilation and installation of the 3 files. Then, we move the 3 tar files that we just downloaded in this folder :
 sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .
 Unpack the 3 tar files :
 sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*
 We compile and install alsa-driver :
 cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install
 We compile and install alsa-lib :
 cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
 We compile and install alsa-utils :
 cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
 Then, we remove the 3 tar files in our personal folder that are not anymore necessary :
 rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*


======================

Then, just restart your computer and your alsa version should be 1.0.19!
 You can verify that you have now indeed have this version of alsa :


 cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.19.
Compiled on May  1 2009 for kernel 2.6.28-11-generic (SMP).

---

