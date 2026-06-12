---
title: "i cant see any videos online"
date: 2008-09-16
forum: Multimedia Software
---

### Post by douggiephresh on 2008-09-16
I cant see any online video sites (youtube, etc) What do  I have to do.

---

### Post by wolfen69 on 2008-09-16
```
sudo apt-get install flashplugin-nonfree
```make sure to have all repos enabled first. (system>administration>software sources)

---

### Post by douggiephresh on 2008-09-16
doug@doug-laptop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for doug: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libxml-sax-perl libxml-namespacesupport-perl libxml-libxml-perl
  libxml-libxml-common-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
doug@doug-laptop:~$ 
doug@doug-laptop:~$

---

### Post by wolfen69 on 2008-09-16
for good measure, do also:```
sudo apt-get install libflashsupport
```

---

