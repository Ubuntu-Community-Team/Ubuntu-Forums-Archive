---
title: "ATI HD 2900 XT and Ubuntu = Hell?"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by ishu on 2007-12-07
Let me start by saying I'm a total noob when it comes to linux so you'll have to bare with me.

I installed ubuntu 7.10 with no problems, everything seems to working fine with the expection of my video card (ATI HD 2900 XT), i followed these instructions  ([http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)) from the unofficial ATI Linux Wiki  5 or so times with out any luck. After completing the instructions

My resolution is proper, but the refresh rate is really bad, when scolling through text or moving a window around the screen. Also when i go to enable multimedia effects in ubuntu my screen turns white, i can still alt+tab so the system is not frozen or locked up. Anyways it's been about of week of trying fresh installs and different guides around the web. I'm having a terrible time any help would be appreciated. 

Thanks

---

### Post by ishu on 2007-12-07
cough bump

---

### Post by ishu on 2007-12-08
bump cough

---

### Post by Melcar on 2007-12-08
Are you using Comipz with AIGLX?  That alone causes some major headaches with the new drivers.  As for installation, have you tried running the installer (not the package generation)?  I have started installing my drivers that way and have been having 100% success rate so far.  You basically follow the "method 2" described on the link you posted, but instead of doing a --buildpkg you just run the installer and follow the automatic install option from there.  Once it finishes, initialize the driver with aticonfig (better to make the changes manually thought).  Another thing I found useful, was not to blacklist fglrx in /etc/default/linux-restricted-modules-common, unless you have installed ATI drivers from the repos before.

---

### Post by ishu on 2007-12-08
thanks for the tips, i'm going to give it a try again.

---

