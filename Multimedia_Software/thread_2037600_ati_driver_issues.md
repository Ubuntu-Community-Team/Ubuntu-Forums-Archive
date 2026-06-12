---
title: "ati driver issues"
date: 2012-08-05
forum: Multimedia Software
---

### Post by SirethSargas on 2012-08-05
hello all. I have recently decided to use ubuntu as my os on my desktop pc. i love the customization and how less resources it takes from the pc. so far i prefer it to other os'. 
my problem is my ati card a 9600 series radeon. i cannot seem to get it to work.

* i have a ati catylsyt control center on my system, but when i click on it, it tells me that i do not have a supported card to run it. 
* whenever i go to additional drivers, it tells me i " no proprietary drivers are in use on this system"
* i have tried to look at tutorials online on how to fix this issue, but most of them vaguely describe steps, assuming i have a decent amount of ubuntu knowledge and i get stuck trying to figure how to do a step.
* i have tried ubuntu software center and searching fglrx but it only brings up the additional drivers which is checked cause i already have it. 
* i am running ubuntu 11.04 desktop. i have a large amount of computer knowledge, mostly in windows, which is apparent is useless in ubuntu rofl.

any help would be appreciated. i would like to keep ubuntu, but with no graphics driver, it is tempting to not use.......

---

### Post by QIII on 2012-08-05
Your graphics chipset is fairly old?

That chipset is no longer supported by the current crop of ATI drivers for Linux and the "legacy" driver will not work with recent versions of X post-2008.

Continue to use the open source Radeon driver which, although it may not have the breadth of features of the proprietary driver, is quite good.

A list of "legacy" cards can be found [here](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx).

---

