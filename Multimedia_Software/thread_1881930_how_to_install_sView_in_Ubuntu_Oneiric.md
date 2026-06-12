---
title: "how to install sView in Ubuntu Oneiric"
date: 2011-11-16
forum: Multimedia Software
---

### Post by Mr_Bumpy on 2011-11-16
[sView 2009]("http://www.sview.ru/en") is a stereoscopic image viewer and movie player that runs on Linux, but hasn't been updated to use the libav libraries included with Ubuntu Oneiric (libavcodec53 vs. libavcodec52).

I have provided a tarball with everything you'll need to get sView working in Oneiric.  [Get it here]("http://www.mediafire.com/?z8a87bx5runzmc1").

WARNING: Do these steps at your own risk!  I can't guarantee them to be foolproof!

First, extract the downloaded archive, then:

1. From within the "amd64" or "i386" folder (whichever pertains to your system), copy the "sView-libs" folder to your home folder.

2. To install sView, double-click the desired .deb package--11.03 for the stable version, 11.07 for the "experimental" version.  If you have any problems with this method, you can also run the following command from the location where the sView .deb files are:
```
sudo dpkg -i sView_11.03.13-1_amd64.deb
```

Of course, type the correct file name for the package you want to install.

3. Modify the launchers replacing "sView" with "LD_LIBRARY_PATH=$HOME/sView-libs sView".  Kubuntu users can simply right-click the K-menu and select "Edit Applications...", then edit the sView launchers in "Multimedia".  I'm not sure what you Ubuntu folk have to do to accomplish the same task, but it might involve editing the "sViewIV.desktop" and "sViewMP.desktop" files in /usr/share/applications.

I hope this helps someone!

---

