---
title: "unable to remove irmp3"
date: 2008-11-01
forum: Multimedia Software
---

### Post by Zigsaw on 2008-11-01
harish@harish-desktop:~$ sudo apt-get remove -f irmp3
[sudo] password for harish: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfreebob0 libresid-builder0c2a libjack0 libtagc0 libsidutils0 libsidplay2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  irmp3
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 393kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122585 files and directories currently installed.)
Removing irmp3 ...
Stopping irmp3: invoke-rc.d: initscript irmp3, action "stop" failed.
dpkg: error processing irmp3 (--remove):
 subprocess pre-removal script returned error exit status 1
Starting irmp3: irmp3.
Errors were encountered while processing:
 irmp3
E: Sub-process /usr/bin/dpkg returned an error code (1)
harish@harish-desktop:~$ 


this is all what happening....:confused::confused:

help plzzz

---

