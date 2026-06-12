---
title: "Aptitude error setting up gnome-codec-install"
date: 2010-06-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2010-06-01
Presumably I'm not the only one?

```
paul@maverick:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
The following packages have been kept back:
  gstreamer0.10-plugins-bad gstreamer0.10-plugins-good libsdl1.2debian 
  libsdl1.2debian-pulseaudio libwbclient0 samba-common smbclient winbind{a} 
The following partially installed packages will be configured:
  gnome-codec-install 
0 packages upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up gnome-codec-install (0.4.5ubuntu2) ...
Compiling /usr/lib/python2.4/site-packages/GnomeCodecInstall/PackageWorker.py ...
  File "/usr/lib/python2.4/site-packages/GnomeCodecInstall/PackageWorker.py", line 48
    trans = yield self.client.commit_packages(
                ^
SyntaxError: invalid syntax

pycentral: pycentral pkginstall: error byte-compiling files (8)
pycentral pkginstall: error byte-compiling files (8)
dpkg: error processing gnome-codec-install (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-codec-install
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gnome-codec-install (0.4.5ubuntu2) ...
Compiling /usr/lib/python2.4/site-packages/GnomeCodecInstall/PackageWorker.py ...
  File "/usr/lib/python2.4/site-packages/GnomeCodecInstall/PackageWorker.py", line 48
    trans = yield self.client.commit_packages(
                ^
SyntaxError: invalid syntax

pycentral: pycentral pkginstall: error byte-compiling files (8)
pycentral pkginstall: error byte-compiling files (8)
dpkg: error processing gnome-codec-install (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gnome-codec-install
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done

paul@maverick:~$ 
```

---

### Post by taavikko on 2010-06-01
x86_64 arch update went smoothly few hours ago, no problems here.

---

### Post by paul_in_london on 2010-06-01
Hmm. 32 bit in my case. Never had much luck with x64 on my system. Will have to give that another go sometime.

---

### Post by sasagundul on 2010-06-28
yes. i have the same bug too. 
im upgrading form 10.04 LTS to 10.10 
at the end of aptitude the crash showed up
it says invalid syntax

---

### Post by dino99 on 2010-06-28
apt-get is a better choice IMO, and never run both apt-get & aptitude as they built different indexes

clean the cache and remove/purge (with synaptic) then reinstall the package(s) with issues

---

### Post by paul_in_london on 2010-06-28
I subscribed to this bug at the time:

[https://bugs.launchpad.net/ubuntu/+source/gnome-codec-install/+bug/589746](https://bugs.launchpad.net/ubuntu/+source/gnome-codec-install/+bug/589746)

The **aptitude** messages were becoming a bit irritating and I decided I didn't really need **gnome-codec-install** anyway so I just deleted it.

---

