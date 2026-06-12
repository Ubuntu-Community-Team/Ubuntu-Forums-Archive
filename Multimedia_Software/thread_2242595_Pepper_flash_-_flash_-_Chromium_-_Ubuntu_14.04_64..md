---
title: "Pepper flash - flash - Chromium - Ubuntu 14.04 64.  plugin issue"
date: 2014-09-02
forum: Multimedia Software
---

### Post by xigen on 2014-09-02
Ubuntu 14.04 64

Flash worked last week on both Firefox 31.0 and Chromium Version 36.0.1985.125 Ubuntu 14.04 (283153)

This week Flash works on Firefox, and on Chromium I get the error message: This plug-in is not supported. 

meow@MeowBatunde:~$ sudo apt-get install flashplugin-installer
```
[sudo] password for meow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 35 not upgraded.
```

How do I navigate plug-ins to get flash video to play?

---

### Post by bcschmerker on 2014-09-03
What you need for Chromium™ (package: **chromium-browser**) is Adobe® Flash Player® for Google® Pepper™ API (package: **pepflashplugin-nonfree**):
```
sudo apt-get install pepflashplugin-nonfree

```I have been using it under Ubuntu® 12.04.5-LTS (ppa:skunk/pepper-flash) and have not encountered any problems not already raised at the Google® Forums.

---

### Post by deadflowr on 2014-09-03
Pepperflash is available through the normal repos for trusty, so no need for a ppa.
And it's called **pepper**flashplugin-nonfree, instead of **pep**flashplugin-nonfree.
Just in case you attempt to install it and it tells you no package found.

---

### Post by xigen on 2014-09-03
OK.  All is good and Chrome / flash is working again.

---

