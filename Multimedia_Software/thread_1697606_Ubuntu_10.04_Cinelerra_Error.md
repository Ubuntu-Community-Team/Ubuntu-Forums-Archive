---
title: "Ubuntu 10.04: Cinelerra Error"
date: 2011-03-01
forum: Multimedia Software
---

### Post by SexySara on 2011-03-01
I am getting an error when trying to install and run this program... any ideas? This the install code, then down below this I have added a thumbnail of what its trying to tell me. Every time I try to install a new program now, it keeps giving this code so I just took the program off and everything is fixed, but I would really like to play with this software.

```

~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cinelerra
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/11.4MB of archives.
After this operation, 24.5MB of additional disk space will be used.
Selecting previously deselected package cinelerra.
(Reading database ... 230185 files and directories currently installed.)
Unpacking cinelerra (from .../cinelerra_1%3a2.1.5-0.14~ppa1~lucid1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up cinelerra (1:2.1.5-0.14~ppa1~lucid1) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: error processing cinelerra (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 cinelerra
localepurge: Disk space freed in /usr/share/locale: 648 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 648 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
~$ 

```

---

