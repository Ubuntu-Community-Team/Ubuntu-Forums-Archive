---
title: "[SOLVED] ATI Radeon Xpress 1150 : no 3D acceleration"
date: 2008-07-10
forum: Multimedia Software
---

### Post by PeterP24 on 2008-07-10
Hi; Although there is plenty of documentation for this video card (ATI Radeon Xpress 1150), I can't install the driver no matter what method I use.
So far I've tried the following methods/guides :
- installing through ubuntu, restricted drivers manager (now hardware drivers) - here I've also tried the instructions provided here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) for Hardy
- through envy;
- through this guide : [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) (method two) - this was the first method I've tried since I wanted the latest driver from ATI.

No matter what I do, after the necessary reboot, I end up with mesa drivers (after 2 days of tests is kind of frustrating).

Any way, at some point (last night) I had the 3D acceleration with the latest ATI driver but I've lost it somehow. At that time fglrx returned the right stuff + something more (segmentation fault) which I've chosed to ignore at that moment. I know it was for real because I was able to run Open Arena.

From that point I've only installed Compiz and that's how I've found out that I don't have Open GL anymore. 
The OS is Ubuntu 8.04 for amd64. 

Any thoughts?
Thank you in advance

Peter

---

### Post by PeterP24 on 2008-07-10
Ah, I've forgot : after installing the latest driver from ati, using this comand : sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb the same sound which you hear at the ubuntu startup is played here. This is kind of weird.

---

### Post by PeterP24 on 2008-07-11
Oh, I've finally got it fixed. For those of you interested here is the link [http://ubuntuforums.org/showthread.php?t=853377&page=4](http://ubuntuforums.org/showthread.php?t=853377&page=4) .

I however have no explanation for that, since I'm a beginner. 

Peter

---

