---
title: "cdrdao gcdmaster and cdrecord for 13.10"
date: 2014-03-22
forum: Multimedia Software
---

### Post by rmstock2 on 2014-03-22
I created a cdrtools package with DVD burning support for 13.10 called OSS DVD extensions for cdrtools 2.0 
( opensource extension to add DVD  support to the cdrtools package) :

[http://crashrecovery.org/oss-dvd/DEB/ubuntu1310/](http://crashrecovery.org/oss-dvd/DEB/ubuntu1310/)
[ftp://ftp.crashrecovery.org/pub/linux/cdrtools/DEB/ubuntu1310/](ftp://ftp.crashrecovery.org/pub/linux/cdrtools/DEB/ubuntu1310/)

To install this run dpkg -i mkisofs_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb cdda2wav_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb . wodim and genisoimage are preserved .

```
total 4204
-rw-r--r--  1 root root  159142 Mar 21 22:14 cdda2wav_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb
-rw-r--r--  1 root root  150868 Mar 22 05:45 cdda2wav_2.01.01a05-0ubuntu1~ossdvd8_i386.deb
-rw-r--r--  1 root root  591212 Mar 21 22:14 cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb
-rw-r--r--  1 root root  582904 Mar 22 05:45 cdrecord_2.01.01a05-0ubuntu1~ossdvd8_i386.deb
-rw-r--r--  1 root root  153332 Mar 21 22:14 cdrtools_2.01.01a05-0ubuntu1~ossdvd8_amd64.build
-rw-r--r--  1 root root    2664 Mar 21 22:14 cdrtools_2.01.01a05-0ubuntu1~ossdvd8_amd64.changes
-rw-r--r--  1 root root   47970 Mar 21 22:12 cdrtools_2.01.01a05-0ubuntu1~ossdvd8.debian.tar.gz
-rw-r--r--  1 root root    1207 Mar 21 22:12 cdrtools_2.01.01a05-0ubuntu1~ossdvd8.dsc
-rw-r--r--  1 root root  148090 Mar 22 05:45 cdrtools_2.01.01a05-0ubuntu1~ossdvd8_i386.build
-rw-r--r--  1 root root    2654 Mar 22 05:45 cdrtools_2.01.01a05-0ubuntu1~ossdvd8_i386.changes
-rw-r--r--  1 root root 1435799 Feb  2  2006 cdrtools_2.01.01a05.orig.tar.bz2
-rw-r--r--  1 root root    1042 Mar 22 05:49 MD5SUM
-rw-r--r--  1 root root  484420 Mar 21 22:14 mkisofs_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb
-rw-r--r--  1 root root  476294 Mar 22 05:45 mkisofs_2.01.01a05-0ubuntu1~ossdvd8_i386.deb
```

```
963dcf057c7d34502bdfa52487dccd5b  cdda2wav_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb
cec1c6205f3c381e2c4f9ca088231b18  cdda2wav_2.01.01a05-0ubuntu1~ossdvd8_i386.deb
d75ea2eec720f6d6bd7bb1569f134757  cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb
8b7e04377c70f84a80c3778fa87b44b8  cdrecord_2.01.01a05-0ubuntu1~ossdvd8_i386.deb
7dc5a42451f94b21a46067b761b9f448  cdrtools_2.01.01a05-0ubuntu1~ossdvd8_amd64.build
452cde485aaecca927b57d22275609f6  cdrtools_2.01.01a05-0ubuntu1~ossdvd8_amd64.changes
4f31b1e83aa9889fbff87fd699c3a184  cdrtools_2.01.01a05-0ubuntu1~ossdvd8.debian.tar.gz
72d39cd9198b0be5a51b8e9fbcdb4d46  cdrtools_2.01.01a05-0ubuntu1~ossdvd8.dsc
aa7c341b6063dc0a9497437d1ce382fa  cdrtools_2.01.01a05-0ubuntu1~ossdvd8_i386.build 
582696083ee779930387e82a143ccdab  cdrtools_2.01.01a05-0ubuntu1~ossdvd8_i386.changes
fb31b2c70b0ed9743f24a5e169569a3e  cdrtools_2.01.01a05.orig.tar.bz2
6af7ef2240cbb3d39f6b4bccec8f1778  mkisofs_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb
034ccd85d012151608cc7247bcf83eac  mkisofs_2.01.01a05-0ubuntu1~ossdvd8_i386.deb
```

Next i created a working version of cdrdao and gcdmaster . Please note that cdrecord and cdrdaowork with
the scsilib library as supplied with the source package. The device mapping then works with libscg and the
linux kernl scsi sg driver module. To my expererience this works brilliantly as almost all CD/DVD  devices 
these days have become scsci driver based, either SATA or USB2 or even USB3.

to install cdrdao and gdcmaster do the following :

from [http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/libgnomemm/](http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/libgnomemm/) :
dpkg -i libgnomemm-2.6-1c2_2.30.0-1_amd64.deb 

from [http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/libgnomeuimm/](http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/libgnomeuimm/) :
dpkg -i libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb

and next from [http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/](http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/)  :
(or here  [ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/](ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/) )

```
total 4660
-rw-r--r--  1 root root  240079 Mar 22 04:33 cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.build
-rw-r--r--  1 root root    2856 Mar 22 04:33 cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.changes
-rw-r--r--  1 root root  552544 Mar 22 04:33 cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb
-rw-r--r--  1 root root   18213 Mar 22 04:27 cdrdao_1.2.3-2ubuntu1~ossdvd8.debian.tar.gz
-rw-r--r--  1 root root    1198 Mar 22 04:27 cdrdao_1.2.3-2ubuntu1~ossdvd8.dsc
-rw-r--r--  1 root root  239489 Mar 22 06:36 cdrdao_1.2.3-2ubuntu1~ossdvd8_i386.build
-rw-r--r--  1 root root    2849 Mar 22 06:36 cdrdao_1.2.3-2ubuntu1~ossdvd8_i386.changes
-rw-r--r--  1 root root  543478 Mar 22 06:36 cdrdao_1.2.3-2ubuntu1~ossdvd8_i386.deb
-rw-r--r--  1 root root 1428695 Oct  6  2009 cdrdao_1.2.3.orig.tar.bz2
-rw-r--r--  1 root root  517280 Mar 22 04:33 gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb
-rw-r--r--  1 root root  516812 Mar 22 06:36 gcdmaster_1.2.3-2ubuntu1~ossdvd8_i386.deb
-rw-r--r--  1 root root  379846 Mar 22 05:08 gcdmaster-ubuntu1310.jpg
-rw-r--r--  1 root root  256889 Mar 22 07:41 gcdmaster-ubuntu1310-s.jpg
drwxr-xr-x  2 root root    4096 Mar 22 06:15 libgnomemm/
drwxr-xr-x  2 root root    4096 Mar 22 06:27 libgnomeuimm/
-rw-r--r--  1 root root     871 Mar 22 06:40 MD5SUM
```

```
ecbeecac55fd7fb186bd1c5772ecb089  cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.build
b56809141e6658601e4e305987d1e570  cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.changes
aaf495202939b28f24dc2fa6b5cfab99  cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb
0c50fbbc6ec93848f76066e22ffdaed6  cdrdao_1.2.3-2ubuntu1~ossdvd8.debian.tar.gz
f0d53d7235f15ab0c6713e3652a45aba  cdrdao_1.2.3-2ubuntu1~ossdvd8.dsc
af6fa5bba8a3e9899e76aed1fe370e05  cdrdao_1.2.3-2ubuntu1~ossdvd8_i386.build
52bc364abf186d589d5de312c697aa8a  cdrdao_1.2.3-2ubuntu1~ossdvd8_i386.changes
d46e5469c3307efd97ff73f1b03b6498  cdrdao_1.2.3-2ubuntu1~ossdvd8_i386.deb
8d15ba6280bb7ba2f4d6be31d28b3c0c  cdrdao_1.2.3.orig.tar.bz2
8f541558e49e558df4714a0e3c403ee4  gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb
4a1315f532637aa0ca9cb2b4666beb02  gcdmaster_1.2.3-2ubuntu1~ossdvd8_i386.deb
e3fa89f1bbd073c37860a37aab7cfbe7  gcdmaster-ubuntu1310.jpg
```

dpkg -i cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb
Selecting previously unselected package cdrdao.
(Reading database ... 271375 files and directories currently installed.)
Unpacking cdrdao (from cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb) ...
Selecting previously unselected package gcdmaster.
Unpacking gcdmaster (from gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb) ...
Setting up cdrdao (1:1.2.3-2ubuntu1~ossdvd8) ...
Setting up gcdmaster (1:1.2.3-2ubuntu1~ossdvd8) ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...

Here's a screenshot :

[IMG]http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/gcdmaster-ubuntu1310-s.jpg[/IMG]

[URL="http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/cdrdao_1.2.3-2ubuntu1%7Eossdvd8_amd64.deb"]
[/URL]

---

### Post by rmstock2 on 2014-03-24
There are some compliations when installing this on a fresh ubuntu 1310 install with recent updates . So
here's the installation logs of how to install cdrecord and cdrdao/gdcmaster :

[http://crashrecovery.org/oss-dvd/DEB/ubuntu1310/install-log-cdrecord.txt](http://crashrecovery.org/oss-dvd/DEB/ubuntu1310/install-log-cdrecord.txt)
```

root@30TG:/home/stock/cdrecord# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  genisoimage wodim
Suggested packages:
  cdrkit-doc
The following NEW packages will be installed:
  genisoimage wodim
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 959 kB of archives.
After this operation, 2463 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://nl.archive.ubuntu.com/ubuntu/ saucy/main genisoimage amd64 9:1.1.11-2ubuntu3 [587 kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ saucy/main wodim amd64 9:1.1.11-2ubuntu3 [372 kB]
Fetched 959 kB in 1s (948 kB/s)
Selecting previously unselected package genisoimage.
(Reading database ... 193151 files and directories currently installed.)
Unpacking genisoimage (from .../genisoimage_9%3a1.1.11-2ubuntu3_amd64.deb) ...
Unpacking wodim (from .../wodim_9%3a1.1.11-2ubuntu3_amd64.deb) ...
Processing triggers for man-db ...
Setting up genisoimage (9:1.1.11-2ubuntu3) ...
Setting up wodim (9:1.1.11-2ubuntu3) ...
root@30TG:/home/stock/cdrecord# 
root@30TG:/home/stock/cdrecord# 
root@30TG:/home/stock/cdrecord# 
root@30TG:/home/stock/cdrecord# 

root@30TG:/home/stock/cdrecord# dpkg -i cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb mkisofs_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb cdda2wav_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb 
Selecting previously unselected package cdrecord.
dpkg: considering removing wodim in favour of cdrecord ...
dpkg: yes, will remove wodim in favour of cdrecord
(Reading database ... 193189 files and directories currently installed.)
Unpacking cdrecord (from cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb) ...
dpkg: error processing cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb (--install):
 trying to overwrite '/usr/bin/devdump', which is also in package genisoimage 9:1.1.11-2ubuntu3
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package mkisofs.
dpkg: considering removing genisoimage in favour of mkisofs ...
dpkg: yes, will remove genisoimage in favour of mkisofs
Unpacking mkisofs (from mkisofs_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb) ...
Selecting previously unselected package cdda2wav.
Unpacking cdda2wav (from cdda2wav_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb) ...
Setting up mkisofs (10:2.01.01a05-0ubuntu1~ossdvd8) ...
Setting up cdda2wav (10:2.01.01a05-0ubuntu1~ossdvd8) ...
Processing triggers for man-db ...
Errors were encountered while processing:
 cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb
root@30TG:/home/stock/cdrecord# dpkg --force-conflicts -i cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb 
(Reading database ... 193174 files and directories currently installed.)
Unpacking cdrecord (from cdrecord_2.01.01a05-0ubuntu1~ossdvd8_amd64.deb) ...
Setting up cdrecord (10:2.01.01a05-0ubuntu1~ossdvd8) ...
Processing triggers for man-db ...
root@30TG:/home/stock/cdrecord#
```

And here the install log for cdrdao en gdcmaster .. ( a couple of dependencies need to be added )
[http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/install-log-cdrdao.txt](http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/install-log-cdrdao.txt)

```

root@30TG:/home/stock/cdrdao# wget ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/libgnomemm/libgnomemm-2.6-1c2_2.30.0-1_amd64.deb
--2014-03-24 13:08:09--  ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/libgnomemm/libgnomemm-2.6-1c2_2.30.0-1_amd64.deb
           => â€˜libgnomemm-2.6-1c2_2.30.0-1_amd64.debâ€™
Resolving ftp.crashrecovery.org (ftp.crashrecovery.org)... 192.168.178.10
Connecting to ftp.crashrecovery.org (ftp.crashrecovery.org)|192.168.178.10|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/linux/mp3-ripkit/cdrdao/ubuntu1310/libgnomemm ... done.
==> SIZE libgnomemm-2.6-1c2_2.30.0-1_amd64.deb ... 20744
==> PASV ... done.    ==> RETR libgnomemm-2.6-1c2_2.30.0-1_amd64.deb ... done.
Length: 20744 (20K) (unauthoritative)

100%[======================================>] 20.744      --.-K/s   in 0,02s   

2014-03-24 13:08:09 (850 KB/s) - â€˜libgnomemm-2.6-1c2_2.30.0-1_amd64.debâ€™ saved [20744]

root@30TG:/home/stock/cdrdao# dpkg -i libgnomemm-2.6-1c2_2.30.0-1_amd64.deb 
Selecting previously unselected package libgnomemm-2.6-1c2.
(Reading database ... 192807 files and directories currently installed.)
Unpacking libgnomemm-2.6-1c2 (from libgnomemm-2.6-1c2_2.30.0-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of libgnomemm-2.6-1c2:
 libgnomemm-2.6-1c2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not installed.
 libgnomemm-2.6-1c2 depends on libgtkmm-2.4-1c2a (>= 1:2.24.0); however:
  Package libgtkmm-2.4-1c2a is not installed.

dpkg: error processing libgnomemm-2.6-1c2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnomemm-2.6-1c2
root@30TG:/home/stock/cdrdao# apt-get install libgnome2-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgnome2-0 : Depends: libbonobo2-0 (>= 2.32.1-0ubuntu1.1) but it is not going to be installed
               Depends: libgnomevfs2-0 (>= 1:2.17.90) but it is not going to be installed
               Depends: liborbit2 (>= 1:2.14.10) but it is not going to be installed
               Depends: libgnome2-common (>= 2.32) but it is not going to be installed
               Depends: libgnome2-common (< 2.33) but it is not going to be installed
               Depends: libgnome2-bin
 libgnomemm-2.6-1c2 : Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@30TG:/home/stock/cdrdao# apt-get install libgnome2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgnome2
root@30TG:/home/stock/cdrdao# apt-get install libgnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgnome
root@30TG:/home/stock/cdrdao# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libbonobo2-0 libbonobo2-common libgnome2-0 libgnome2-bin libgnome2-common
  libgnomevfs2-0 libgnomevfs2-common libgtkmm-2.4-1c2a libidl-common libidl0
  liborbit2
Suggested packages:
  libbonobo2-bin desktop-base libgnomevfs2-bin libgnomevfs2-extra gamin fam
  gnome-mime-data
The following NEW packages will be installed:
  libbonobo2-0 libbonobo2-common libgnome2-0 libgnome2-bin libgnome2-common
  libgnomevfs2-0 libgnomevfs2-common libgtkmm-2.4-1c2a libidl-common libidl0
  liborbit2
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1849 kB of archives.
After this operation, 10,6 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libbonobo2-common all 2.32.1-0ubuntu4 [34,1 kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libidl-common all 0.8.14-0.2ubuntu3 [8536 B]
Get:3 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libidl0 amd64 0.8.14-0.2ubuntu3 [81,6 kB]
Get:4 http://nl.archive.ubuntu.com/ubuntu/ saucy/main liborbit2 amd64 1:2.14.19-0.2 [148 kB]
Get:5 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libbonobo2-0 amd64 2.32.1-0ubuntu4 [214 kB]
Get:6 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnomevfs2-common amd64 1:2.24.4-1ubuntu6 [22,8 kB]
Get:7 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnomevfs2-0 amd64 1:2.24.4-1ubuntu6 [210 kB]
Get:8 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnome2-common all 2.32.1-2ubuntu4 [33,3 kB]
Get:9 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnome2-bin amd64 2.32.1-2ubuntu4 [15,0 kB]
Get:10 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnome2-0 amd64 2.32.1-2ubuntu4 [43,1 kB]
Get:11 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgtkmm-2.4-1c2a amd64 1:2.24.4-1 [1038 kB]
Fetched 1849 kB in 2s (920 kB/s)            
Selecting previously unselected package libbonobo2-common.
(Reading database ... 192817 files and directories currently installed.)
Unpacking libbonobo2-common (from .../libbonobo2-common_2.32.1-0ubuntu4_all.deb) ...
Selecting previously unselected package libidl-common.
Unpacking libidl-common (from .../libidl-common_0.8.14-0.2ubuntu3_all.deb) ...
Selecting previously unselected package libidl0:amd64.
Unpacking libidl0:amd64 (from .../libidl0_0.8.14-0.2ubuntu3_amd64.deb) ...
Selecting previously unselected package liborbit2:amd64.
Unpacking liborbit2:amd64 (from .../liborbit2_1%3a2.14.19-0.2_amd64.deb) ...
Selecting previously unselected package libbonobo2-0:amd64.
Unpacking libbonobo2-0:amd64 (from .../libbonobo2-0_2.32.1-0ubuntu4_amd64.deb) ...
Selecting previously unselected package libgnomevfs2-common.
Unpacking libgnomevfs2-common (from .../libgnomevfs2-common_1%3a2.24.4-1ubuntu6_amd64.deb) ...
Selecting previously unselected package libgnomevfs2-0:amd64.
Unpacking libgnomevfs2-0:amd64 (from .../libgnomevfs2-0_1%3a2.24.4-1ubuntu6_amd64.deb) ...
Selecting previously unselected package libgnome2-common.
Unpacking libgnome2-common (from .../libgnome2-common_2.32.1-2ubuntu4_all.deb) ...
Selecting previously unselected package libgnome2-bin.
Unpacking libgnome2-bin (from .../libgnome2-bin_2.32.1-2ubuntu4_amd64.deb) ...
Selecting previously unselected package libgnome2-0:amd64.
Unpacking libgnome2-0:amd64 (from .../libgnome2-0_2.32.1-2ubuntu4_amd64.deb) ...
Selecting previously unselected package libgtkmm-2.4-1c2a:amd64.
Unpacking libgtkmm-2.4-1c2a:amd64 (from .../libgtkmm-2.4-1c2a_1%3a2.24.4-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Setting up libbonobo2-common (2.32.1-0ubuntu4) ...
Setting up libidl-common (0.8.14-0.2ubuntu3) ...
Setting up libidl0:amd64 (0.8.14-0.2ubuntu3) ...
Setting up liborbit2:amd64 (1:2.14.19-0.2) ...
Setting up libbonobo2-0:amd64 (2.32.1-0ubuntu4) ...
Setting up libgnomevfs2-common (1:2.24.4-1ubuntu6) ...
Setting up libgnomevfs2-0:amd64 (1:2.24.4-1ubuntu6) ...
Setting up libgnome2-common (2.32.1-2ubuntu4) ...
Setting up libgtkmm-2.4-1c2a:amd64 (1:2.24.4-1) ...
Setting up libgnome2-bin (2.32.1-2ubuntu4) ...
Setting up libgnome2-0:amd64 (2.32.1-2ubuntu4) ...
Setting up libgnomemm-2.6-1c2 (2.30.0-1) ...
Processing triggers for libc-bin ...
root@30TG:/home/stock/cdrdao# dpkg -i libgnomemm-2.6-1c2_2.30.0-1_amd64.deb 
(Reading database ... 193002 files and directories currently installed.)
Preparing to replace libgnomemm-2.6-1c2 2.30.0-1 (using libgnomemm-2.6-1c2_2.30.0-1_amd64.deb) ...
Unpacking replacement libgnomemm-2.6-1c2 ...
Setting up libgnomemm-2.6-1c2 (2.30.0-1) ...
Processing triggers for libc-bin ...
root@30TG:/home/stock/cdrdao# wget ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/libgnomeuimm/libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb
--2014-03-24 13:10:08--  ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/libgnomeuimm/libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb
           => â€˜libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.debâ€™
Resolving ftp.crashrecovery.org (ftp.crashrecovery.org)... 192.168.178.10
Connecting to ftp.crashrecovery.org (ftp.crashrecovery.org)|192.168.178.10|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/linux/mp3-ripkit/cdrdao/ubuntu1310/libgnomeuimm ... done.
==> SIZE libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb ... 131066
==> PASV ... done.    ==> RETR libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb ... done.
Length: 131066 (128K) (unauthoritative)

100%[======================================>] 131.066     --.-K/s   in 0,04s   

2014-03-24 13:10:09 (3,54 MB/s) - â€˜libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.debâ€™ saved [131066]

root@30TG:/home/stock/cdrdao# dpkg -i libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb 
Selecting previously unselected package libgnomeuimm-2.6-1c2a.
(Reading database ... 193002 files and directories currently installed.)
Unpacking libgnomeuimm-2.6-1c2a (from libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb) ...
dpkg: dependency problems prevent configuration of libgnomeuimm-2.6-1c2a:
 libgnomeuimm-2.6-1c2a depends on libgconfmm-2.6-1c2 (>= 2.24.0); however:
  Package libgconfmm-2.6-1c2 is not installed.
 libgnomeuimm-2.6-1c2a depends on libgnome-vfsmm-2.6-1c2a (>= 2.22.0); however:
  Package libgnome-vfsmm-2.6-1c2a is not installed.
 libgnomeuimm-2.6-1c2a depends on libgnomecanvas2-0 (>= 2.11.1); however:
  Package libgnomecanvas2-0 is not installed.
 libgnomeuimm-2.6-1c2a depends on libgnomecanvasmm-2.6-1c2a (>= 2.23.1); however:
  Package libgnomecanvasmm-2.6-1c2a is not installed.
 libgnomeuimm-2.6-1c2a depends on libgnomeui-0 (>= 2.22.0); however:
  Package libgnomeui-0 is not installed.

dpkg: error processing libgnomeuimm-2.6-1c2a (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgnomeuimm-2.6-1c2a
root@30TG:/home/stock/cdrdao# apt-get install libgconfmm-2.6-1c2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgnomeuimm-2.6-1c2a : Depends: libgnome-vfsmm-2.6-1c2a (>= 2.22.0) but it is not going to be installed
                         Depends: libgnomecanvas2-0 (>= 2.11.1) but it is not going to be installed
                         Depends: libgnomecanvasmm-2.6-1c2a (>= 2.23.1) but it is not going to be installed
                         Depends: libgnomeui-0 (>= 2.22.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@30TG:/home/stock/cdrdao# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libbonoboui2-0 libbonoboui2-common libgconf2-4 libgconfmm-2.6-1c2
  libglade2-0 libgnome-vfsmm-2.6-1c2a libgnomecanvas2-0 libgnomecanvas2-common
  libgnomecanvasmm-2.6-1c2a libgnomeui-0 libgnomeui-common
The following NEW packages will be installed:
  libbonoboui2-0 libbonoboui2-common libgconf2-4 libgconfmm-2.6-1c2
  libglade2-0 libgnome-vfsmm-2.6-1c2a libgnomecanvas2-0 libgnomecanvas2-common
  libgnomecanvasmm-2.6-1c2a libgnomeui-0 libgnomeui-common
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 813 kB of archives.
After this operation, 3492 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe libgconfmm-2.6-1c2 amd64 2.28.3-0ubuntu1 [28,8 kB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgconf2-4 amd64 3.2.6-0ubuntu1 [2046 B]
Get:3 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe libgnome-vfsmm-2.6-1c2a amd64 2.26.0-1build1 [71,6 kB]
Get:4 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libglade2-0 amd64 1:2.6.4-1ubuntu3 [44,5 kB]
Get:5 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnomecanvas2-common all 2.30.3-1ubuntu2 [9108 B]
Get:6 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnomecanvas2-0 amd64 2.30.3-1ubuntu2 [101 kB]
Get:7 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe libgnomecanvasmm-2.6-1c2a amd64 2.26.0-1build1 [80,4 kB]
Get:8 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libbonoboui2-common all 2.24.5-0ubuntu2 [11,7 kB]
Get:9 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libbonoboui2-0 amd64 2.24.5-0ubuntu2 [189 kB]
Get:10 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnomeui-common all 2.24.5-2ubuntu3 [16,6 kB]
Get:11 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libgnomeui-0 amd64 2.24.5-2ubuntu3 [258 kB]
Fetched 813 kB in 1s (593 kB/s)       
Selecting previously unselected package libgconfmm-2.6-1c2.
(Reading database ... 193011 files and directories currently installed.)
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.28.3-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libgconf2-4:amd64.
Unpacking libgconf2-4:amd64 (from .../libgconf2-4_3.2.6-0ubuntu1_amd64.deb) ...
Selecting previously unselected package libgnome-vfsmm-2.6-1c2a.
Unpacking libgnome-vfsmm-2.6-1c2a (from .../libgnome-vfsmm-2.6-1c2a_2.26.0-1build1_amd64.deb) ...
Selecting previously unselected package libglade2-0:amd64.
Unpacking libglade2-0:amd64 (from .../libglade2-0_1%3a2.6.4-1ubuntu3_amd64.deb) ...
Selecting previously unselected package libgnomecanvas2-common.
Unpacking libgnomecanvas2-common (from .../libgnomecanvas2-common_2.30.3-1ubuntu2_all.deb) ...
Selecting previously unselected package libgnomecanvas2-0:amd64.
Unpacking libgnomecanvas2-0:amd64 (from .../libgnomecanvas2-0_2.30.3-1ubuntu2_amd64.deb) ...
Selecting previously unselected package libgnomecanvasmm-2.6-1c2a.
Unpacking libgnomecanvasmm-2.6-1c2a (from .../libgnomecanvasmm-2.6-1c2a_2.26.0-1build1_amd64.deb) ...
Selecting previously unselected package libbonoboui2-common.
Unpacking libbonoboui2-common (from .../libbonoboui2-common_2.24.5-0ubuntu2_all.deb) ...
Selecting previously unselected package libbonoboui2-0:amd64.
Unpacking libbonoboui2-0:amd64 (from .../libbonoboui2-0_2.24.5-0ubuntu2_amd64.deb) ...
Selecting previously unselected package libgnomeui-common.
Unpacking libgnomeui-common (from .../libgnomeui-common_2.24.5-2ubuntu3_all.deb) ...
Selecting previously unselected package libgnomeui-0:amd64.
Unpacking libgnomeui-0:amd64 (from .../libgnomeui-0_2.24.5-2ubuntu3_amd64.deb) ...
Setting up libgconfmm-2.6-1c2 (2.28.3-0ubuntu1) ...
Setting up libgconf2-4:amd64 (3.2.6-0ubuntu1) ...
Setting up libgnome-vfsmm-2.6-1c2a (2.26.0-1build1) ...
Setting up libglade2-0:amd64 (1:2.6.4-1ubuntu3) ...
Setting up libgnomecanvas2-common (2.30.3-1ubuntu2) ...
Setting up libgnomecanvas2-0:amd64 (2.30.3-1ubuntu2) ...
Setting up libgnomecanvasmm-2.6-1c2a (2.26.0-1build1) ...
Setting up libbonoboui2-common (2.24.5-0ubuntu2) ...
Setting up libbonoboui2-0:amd64 (2.24.5-0ubuntu2) ...
Setting up libgnomeui-common (2.24.5-2ubuntu3) ...
Setting up libgnomeui-0:amd64 (2.24.5-2ubuntu3) ...
Setting up libgnomeuimm-2.6-1c2a (2.28.0-1) ...
Processing triggers for libc-bin ...
root@30TG:/home/stock/cdrdao# dpkg -i libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb (Reading database ... 193106 files and directories currently installed.)
Preparing to replace libgnomeuimm-2.6-1c2a 2.28.0-1 (using libgnomeuimm-2.6-1c2a_2.28.0-1_amd64.deb) ...
Unpacking replacement libgnomeuimm-2.6-1c2a ...
Setting up libgnomeuimm-2.6-1c2a (2.28.0-1) ...
Processing triggers for libc-bin ...
root@30TG:/home/stock/cdrdao# wget ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb
--2014-03-24 13:12:08--  ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb
           => â€˜cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.debâ€™
Resolving ftp.crashrecovery.org (ftp.crashrecovery.org)... 192.168.178.10
Connecting to ftp.crashrecovery.org (ftp.crashrecovery.org)|192.168.178.10|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/linux/mp3-ripkit/cdrdao/ubuntu1310 ... done.
==> SIZE cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb ... 552544
==> PASV ... done.    ==> RETR cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb ... done.
Length: 552544 (540K) (unauthoritative)

100%[======================================>] 552.544     --.-K/s   in 0,05s   

2014-03-24 13:12:08 (10,2 MB/s) - â€˜cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.debâ€™ saved [552544]

root@30TG:/home/stock/cdrdao# wget ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb
--2014-03-24 13:12:23--  ftp://ftp.crashrecovery.org/pub/linux/mp3-ripkit/cdrdao/ubuntu1310/gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb
           => â€˜gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.debâ€™
Resolving ftp.crashrecovery.org (ftp.crashrecovery.org)... 192.168.178.10
Connecting to ftp.crashrecovery.org (ftp.crashrecovery.org)|192.168.178.10|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD (1) /pub/linux/mp3-ripkit/cdrdao/ubuntu1310 ... done.
==> SIZE gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb ... 517280
==> PASV ... done.    ==> RETR gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb ... done.
Length: 517280 (505K) (unauthoritative)

100%[======================================>] 517.280     --.-K/s   in 0,01s   

2014-03-24 13:12:23 (33,2 MB/s) - â€˜gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.debâ€™ saved [517280]

root@30TG:/home/stock/cdrdao# dpkg -i cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb 
Selecting previously unselected package cdrdao.
(Reading database ... 193106 files and directories currently installed.)
Unpacking cdrdao (from cdrdao_1.2.3-2ubuntu1~ossdvd8_amd64.deb) ...
Selecting previously unselected package gcdmaster.
Unpacking gcdmaster (from gcdmaster_1.2.3-2ubuntu1~ossdvd8_amd64.deb) ...
dpkg: dependency problems prevent configuration of cdrdao:
 cdrdao depends on libao4 (>= 1.1.0); however:
  Package libao4 is not installed.
 cdrdao depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not installed.
 cdrdao depends on libmp3lame0; however:
  Package libmp3lame0 is not installed.

dpkg: error processing cdrdao (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gcdmaster:
 gcdmaster depends on libao4 (>= 1.1.0); however:
  Package libao4 is not installed.
 gcdmaster depends on libglademm-2.4-1c2a (>= 2.6.0); however:
  Package libglademm-2.4-1c2a is not installed.
 gcdmaster depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not installed.

dpkg: error processing gcdmaster (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Errors were encountered while processing:
 cdrdao
 gcdmaster
root@30TG:/home/stock/cdrdao# apt-get install libao4 libmad0 libmp3lame0 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 gcdmaster : Depends: libglademm-2.4-1c2a (>= 2.6.0) but it is not going to be installed
 libao4 : Depends: libao-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@30TG:/home/stock/cdrdao# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libao-common libao4 libglademm-2.4-1c2a libmad0 libmp3lame0
Suggested packages:
  libesd0 libesd-alsa0
The following NEW packages will be installed:
  libao-common libao4 libglademm-2.4-1c2a libmad0 libmp3lame0
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 327 kB of archives.
After this operation, 914 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libao-common all 1.1.0-2ubuntu1 [6610 B]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ saucy/main libao4 amd64 1.1.0-2ubuntu1 [39,8 kB]
Get:3 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe libmad0 amd64 0.15.1b-7ubuntu2 [72,1 kB]
Get:4 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe libmp3lame0 amd64 3.99.5+repack1-3 [186 kB]
Get:5 http://nl.archive.ubuntu.com/ubuntu/ saucy/universe libglademm-2.4-1c2a amd64 2.6.7-2build1 [22,2 kB]
Fetched 327 kB in 0s (374 kB/s)               
Selecting previously unselected package libao-common.
(Reading database ... 193152 files and directories currently installed.)
Unpacking libao-common (from .../libao-common_1.1.0-2ubuntu1_all.deb) ...
Selecting previously unselected package libao4:amd64.
Unpacking libao4:amd64 (from .../libao4_1.1.0-2ubuntu1_amd64.deb) ...
Selecting previously unselected package libmad0:amd64.
Unpacking libmad0:amd64 (from .../libmad0_0.15.1b-7ubuntu2_amd64.deb) ...
Selecting previously unselected package libmp3lame0:amd64.
Unpacking libmp3lame0:amd64 (from .../libmp3lame0_3.99.5+repack1-3_amd64.deb) ...
Selecting previously unselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-2build1_amd64.deb) ...
Processing triggers for man-db ...
Setting up libao-common (1.1.0-2ubuntu1) ...
Setting up libao4:amd64 (1.1.0-2ubuntu1) ...
Setting up libmad0:amd64 (0.15.1b-7ubuntu2) ...
Setting up libmp3lame0:amd64 (3.99.5+repack1-3) ...
Setting up cdrdao (1:1.2.3-2ubuntu1~ossdvd8) ...
Setting up libglademm-2.4-1c2a (2.6.7-2build1) ...
Setting up gcdmaster (1:1.2.3-2ubuntu1~ossdvd8) ...
Processing triggers for libc-bin ...
root@30TG:/home/stock/cdrdao# 

```

After that gcdmaster works like expected :

[http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/Screenshot-from-2014-03-24-13.34.07-1.png](http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/Screenshot-from-2014-03-24-13.34.07-1.png)

---

### Post by rmstock2 on 2014-04-10
Here's a more readable installation log :

[http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/install-log-cdrdao.html](http://crashrecovery.org/mp3-ripkit/cdrdao/ubuntu1310/install-log-cdrdao.html)

---

