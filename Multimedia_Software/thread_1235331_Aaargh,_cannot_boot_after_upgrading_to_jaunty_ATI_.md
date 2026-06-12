---
title: "Aaargh, cannot boot after upgrading to jaunty ATI drivers"
date: 2009-08-09
forum: Multimedia Software
---

### Post by KaYnemO on 2009-08-09
Hey all. Just upgraded to jaunty and after a reboot I cannot get even to the login screen - the screen is all scrambled !!! I got ati radeon mobility x1600 card. The weird thing While using the live cd to test the jaunty everything worked flawlessly including compiz etc. Please help - I cannot even get to safemode anymore !!! Also what is the driver the live cd chooses for my card - it works awesome: fps is excellent, compiz and all just flies !!

---

### Post by markbuntu on 2009-08-09
this can happen if you did not remove the ati proprietary driver before upgrading. The driver you were using is not compatible with the Jaunty kernel and the driver that does support the Jaunty kernel does not support your card. The live cd was most likely using the open source ati driver which is vastly improved for your card.

That said. You need to remove the fglrx driver completely and its kernel modules

sudo apt-get purge fglrx*

If you were using a driver from the ati site you can try the uninstall script 

usr/share/ati/fglrx-uninstall.sh

It is important to remove the fglrx driver because some of its files conflict with the ati driver files,

There is more on all that here
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

