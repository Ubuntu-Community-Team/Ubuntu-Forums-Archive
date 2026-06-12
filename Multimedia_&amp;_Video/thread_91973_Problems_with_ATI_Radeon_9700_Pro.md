---
title: "Problems with ATI Radeon 9700 Pro"
date: 2005-11-18
forum: Multimedia &amp; Video
---

### Post by verybloody on 2005-11-18
Hi, 
I installed ubuntu yesturday and i am not familiar with linux or other OS, and I have experienced some problems with installing my video-card correctly. I have an ATI Radeon 9700 pro mobility on a Pentium M 1.6 GH labtop WIDESCREEN (with 1gb ram, not that it matters) 

Anyway, i tried to install the 8.16.20 ATI driver and after some hassle and a good how to: guide i succeded. But now i have a new problem, it won't let me increase beyond 1024x768. I was told that if i changed my xorg modes It would work, so i did ... but it did not. I used nano /etc/X11/xorg.conf and added "1280x800" FIRST at all the depths, saved and then rebooted. I still had the same problem, nothing seemed to have changed. Then I read that there was a common widescreen bug in 8.16.20 driver, so instead i tried to install 8.19.10 driver from a how to guide ( [http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589) ). 

First i removed the previous one by 

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove fglrx-control
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #Select the ATI driver

then i rebooted downloaded the 32bit driver from ATI.com and followed with these steps:

(I am now in the directory with the downloaded file)

sudo apt-get install gcc-3.4 module-assistant build-essential fakeroot dh-make debconf libstdc++5 gcc-3.3-base
sudo sh ./ati-driver-installer-8.19.10-i386.run --buildpkg Ubuntu/breezy
(these steps worked all fine and everything was looking good)
then i tried to write :

sudo dpkg -i xorg-driver-fglrx_8.19.10-1_i386.deb

but it respond with 
error during process of xorg-driver-fglrx_8.19.10-1_i386.deb (--install): can't access archive: no such file or catalog (translated from danish)

What to do ?

If anyone can help me I would more than appreciate it, and since I am unfamiliar with ubuntu i would also apreciate if you wrote it step-by-step =)

/Verybloody

---

### Post by mlomker on 2005-11-18
Are the DEB files in that directory?  If the .run step finished then it would have told you that it created the files.

---

