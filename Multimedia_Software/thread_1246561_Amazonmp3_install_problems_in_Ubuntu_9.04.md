---
title: "Amazonmp3 install problems in Ubuntu 9.04"
date: 2009-08-21
forum: Multimedia Software
---

### Post by glocktop on 2009-08-21
In 9.04 I cannot get it to install successfully, and Amazon.com is non-responsive.

```

root@glockpad:/home/user/Desktop# dpkg -i amazonmp3.deb 
(Reading database ... 165757 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.3-1 (using amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
dpkg: dependency problems prevent configuration of amazonmp3:
 amazonmp3 depends on libboost-thread1.33.1; however:
  Package libboost-thread1.33.1 is not installed.
 amazonmp3 depends on libboost-iostreams1.33.1; however:
  Package libboost-iostreams1.33.1 is not installed.
 amazonmp3 depends on libboost-signals1.33.1; however:
  Package libboost-signals1.33.1 is not installed.
 amazonmp3 depends on libboost-date-time1.33.1; however:
  Package libboost-date-time1.33.1 is not installed.
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Errors were encountered while processing:
 amazonmp3

```I tried all the tricks I know:
```

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  amazonmp3
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 774kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```I referred to [http://ubuntuforums.org/showthread.php?t=559952&page=6](http://ubuntuforums.org/showthread.php?t=559952&page=6) which suggests using getlibs, but that failed too.

```

root@glockpad:/home/user/chroot# dpkg -i /home/user/Desktop/getlibs-all.deb  
Selecting previously deselected package getlibs.
(Reading database ... 165756 files and directories currently installed.)
Unpacking getlibs (from .../user/Desktop/getlibs-all.deb) ...
Setting up getlibs (2.06) ...
root@glockpad:/home/user/chroot# getlibs /usr/bin/amazonmp3 
No match for libboost_date_time-gcc-mt-1_33_1.so.1.33.1
No match for libboost_signals-gcc-mt-1_33_1.so.1.33.1
No match for libboost_iostreams-gcc-mt-1_33_1.so.1.33.1
No match for libboost_thread-gcc-mt-1_33_1.so.1.33.1

```I referred to a chroot solution, but again apt could not install the libboost etc dependcies: [http://slacy.com/blog/2009/08/running-amazonmp3-downloader-on-ubuntu-9-04-amd64-jaunty-via-a-chroot/](http://slacy.com/blog/2009/08/running-amazonmp3-downloader-on-ubuntu-9-04-amd64-jaunty-via-a-chroot/)

In short, I am in dependency hell and it seems like nobody else is? I can't find any solutions.

Link to Amazonmp3 package:  [http://www.amazon.com/gp/dmusic/help/amd.html/ref=sv_dmusic_3](http://www.amazon.com/gp/dmusic/help/amd.html/ref=sv_dmusic_3)

---

