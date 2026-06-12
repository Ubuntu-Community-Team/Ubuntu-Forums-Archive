---
title: "Gstreamer missing plugin - won't play DVDs"
date: 2009-11-01
forum: Multimedia Software
---

### Post by noshooz on 2009-11-01
Running 9.10, tried to play a DVD movie in Movie Player, it won't even start. It gives an error message "Your Gstreamer installation is missing a plugin." What plugin might be missing and how do I get it???

---

### Post by b0b138 on 2009-11-01
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by noshooz on 2009-11-01
Sorry. That link didn't help. Still getting the 'missing plug-in' error. 

Here are the terminal results of running the commands recommended:

bill@ubuntu:~$ sudo apt-get install libdvdread4
[sudo] password for bill: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
libdvdread4 set to manually installed.
The following packages were automatically installed and are no longer required:
  binutils-static
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

bill@ubuntu:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2009-11-01 18:28:13--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11, 88.191.79.39
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36812 (36K) [application/octet-stream]
Saving to: `/tmp/dvdcss-4IZxKF/libdvdcss.deb'

100%[======================================>] 36,812      55.9K/s   in 0.6s    

2009-11-01 18:28:15 (55.9 KB/s) - `/tmp/dvdcss-4IZxKF/libdvdcss.deb' saved [36812/36812]

Selecting previously deselected package libdvdcss2.
(Reading database ... 127475 files and directories currently installed.)
Unpacking libdvdcss2 (from .../dvdcss-4IZxKF/libdvdcss.deb) ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by noshooz on 2009-11-03
SOLVED! Thanks to the Software Center! I installed the GStreamer extra plugins via the Ubuntu Software Center. :D

---

