---
title: "Cinelerra and Localepurge"
date: 2011-10-02
forum: Multimedia Software
---

### Post by headvampyre@hotmail.co.uk on 2011-10-02
Hi, I'm having an issue with Cinelerra installing due to Localepurge removing the German keyboard mapping. 

> apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  cinelerra
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/11.3 MB of archives.
After this operation, 25.5 MB of additional disk space will be used.
Selecting previously deselected package cinelerra.
(Reading database ... 247419 files and directories currently installed.)
Unpacking cinelerra (from .../cinelerra_1%3a2.1.5-0.16~ppa1~natty5_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for python-support ...
Setting up cinelerra (1:2.1.5-0.16~ppa1~natty5) ...
cannot open locale definition file `de_DE': No such file or directory
dpkg: error processing cinelerra (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 cinelerra
localepurge: Disk space freed in /usr/share/locale: 616 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 616 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)

Would there be any way to get past this? If not, would it be possible to just temporarily copy the keyboard mapping?

---

