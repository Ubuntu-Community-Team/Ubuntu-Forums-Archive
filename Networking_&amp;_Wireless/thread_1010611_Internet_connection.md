---
title: "Internet connection"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by dennis0623 on 2008-12-13
I installed Ubuntu 8.1 a couple of days ago and cannot get my wireless Internet card to work.  The card from Alltel is the Huawei EC228 and is for Windows XP, Windows Vista which I am using and the Mac OSX 10.4 or higher.  Am I to assume it will not work on the Linux platform.  Ubuntu recognizes the card but I cannot configure it to work.  Any help will be appreciated.

---

### Post by Martje_001 on 2008-12-14
From [here](http://82.93.77.136/mbastiaan/forums/deb/) download the following packages (with Windows or something):

32-bit:
```
ndisgtk_0.8.3-1_i386.deb
ndiswrapper-common_1.50-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb
```
64-bit:
```
ndisgtk_0.8.3-1_amd64.deb
ndiswrapper-common_1.50-1ubuntu1_all.deb
ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb
```
. Put them on an USB-drive and plug it in in Ubuntu. Install the packages (they need to be installed in a specific order, you'll find out ;)) and run the ndiswrapper GUI (under System, it's called Windows Wireless Drivers or something).

Put in the disk where the windows drivers are on and search for an .inf file. Give it to the GUI and then you should be able to configure your card!

Edit: [Much more information](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jskiddy19 on 2008-12-19
Tried this and nothing worked.  Anymore ideas?
The disk only had one .inf and it was the autorun file.

---

