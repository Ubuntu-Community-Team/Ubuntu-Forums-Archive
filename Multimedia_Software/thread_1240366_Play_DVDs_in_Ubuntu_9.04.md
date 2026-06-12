---
title: "Play DVDs in Ubuntu 9.04"
date: 2009-08-14
forum: Multimedia Software
---

### Post by tostrye on 2009-08-14
I have Ubuntu 9.04 and I am trying to watch Madea Goes to Jail. I did [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) that tutorial, and here are my results:
> $ sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl swh-plugins qjackctl sndfile-programs linux-headers-2.6.28-11
  liblo0ldbl libdjconsole0 nted-doc linux-headers-2.6.28-11-generic flac
  libdjconsole-data rosegarden-data jackd libid3-3.8.3c2a libmpeg3-1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tomas@tomas-desktop:~$  sudo /usr/share/doc/libdvdread4/install-css.sh
--2009-08-14 15:40:20--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11, 91.121.62.209, 88.191.79.39
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36812 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-ZdYRdJ/libdvdcss.deb'

100%[======================================>] 36,812       107K/s   in 0.3s    

2009-08-14 15:40:20 (107 KB/s) - `/tmp/dvdcss-ZdYRdJ/libdvdcss.deb' saved [36812/36812]

Selecting previously deselected package libdvdcss2.
(Reading database ... 183573 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-ZdYRdJ/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
I still can't play Madea Goes to Jail. I've tried Totem and VLC.

---

