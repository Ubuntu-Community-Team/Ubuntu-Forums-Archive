---
title: "Can't Fetch flashplugin-nonfree or installer"
date: 2011-02-12
forum: Multimedia Software
---

### Post by Rasheeke on 2011-02-12
I installed Ubuntu the other day and went to install restricted extras last night.  I get the following 404 errors and I think the problem is not on my end since every other update works fine.  


---@hal:~$ sudo apt-get install flashplugin-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386 nspluginwrapper
Suggested packages:
  xulrunner-1.9 firefox-3.0 konqueror-nsplugins msttcorefonts ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs lib32asound2-plugins
The following NEW packages will be installed:
  flashplugin-installer ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386 nspluginwrapper
0 upgraded, 11 newly installed, 0 to remove and 1 not upgraded.
Need to get 20.0kB/38.5MB of archives.
After this operation, 160MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse flashplugin-installer amd64 10.1.102.65ubuntu0.10.10.1
  404  Not Found [IP: 91.189.88.30 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse flashplugin-installer amd64 10.1.102.65ubuntu0.10.10.1
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.102.65ubuntu0.10.10.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.102.65ubuntu0.10.10.1_amd64.deb) 404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.

---

### Post by gordintoronto on 2011-02-12
I suggest using Synaptic Package Manager, and changing the "Download From" option. It's under Settings/Repositories. Then Reload, then search for flashplugin.

---

