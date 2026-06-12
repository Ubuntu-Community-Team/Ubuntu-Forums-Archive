---
title: "Flash and compiz newbie"
date: 2010-05-13
forum: Multimedia Software
---

### Post by osomphane on 2010-05-13
Hi all, I have seen a lot of threads about this and the information is getting a bit mixed up in my head with the old and new threads. Can anyone help a newbie out?

I am having a problem with full screen 480p tearing on the Hulu website. The tearing seems less pronounced if I do not have full screen or 480p enabled. I have the following:

[LIST=1]
[*]Clean 10.04 install
[*]"Adobe Flash plugin" installed from the Ubuntu Software Center
[*]ATI Hardware Drivers enabled and vsync is set to always on (3d tab, though)
[*]System > Preferences > Appearance is set to no desktop effects
[*]Asus N81VP laptop - T9600 + ATI4650
[/LIST]
I saw the following website with a recent guide: [http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

Under 32bit, it suggested removing some packages and installing a different adobe flash package. Would anyone recommend that? In the software center, there is both "Adobe Flash plugin" and "Adobe Flash Plugin 10" and "Adobe Flash Player plugin installer (transitional package)". What is the difference between these three and is there a reason why the guide would suggest the last one?

Under Compiz, it says to go to “System >> Preferences  >> CompizConfig  Settings Manager  >> General Options >>  General”. However, I do not have that menu available. I have disabled the desktop effects in appearance. Do I need to do anything more to disable compiz? Is disabling compiz even advisable?

Any other recommendations?

---

### Post by xzero1 on 2010-05-13
Visual effects off => no compiz. I have gotten perfect video playback using the stock radeon drivers with 10.04 on my hd 4770. You can test this using the live cd and simply installing adobe flash. If you install ati proprietary drivers then you will probably find issues. This post addresses some of them: [http://ubuntuforums.org/showthread.php?t=1385896]("http://ubuntuforums.org/showthread.php?t=1385896")

---

### Post by andrea000 on 2010-05-13
if you have removed compiz config setting manager then no nothing
else is needed as far as i know and now on flash i would recommend
installing flash from the adobe website i think it works better.

---

### Post by osomphane on 2010-05-15
When you say install flash from Adobe's website, do I use the following link?

I found it under Install a different version of Adobe Flash Player > APT for Ubuntu 9.04+:
apt:adobe-flashplugin?channel=$distro-partner

There is also a .deb and .tar.gz., and then a 10.1 rc4. Any recommendations?

---

### Post by xzero1 on 2010-05-15
> **osomphane said:**
> When you say install flash from Adobe's website, do I use the following link?

I found it under Install a different version of Adobe Flash Player > APT for Ubuntu 9.04+:
apt:adobe-flashplugin?channel=$distro-partner

There is also a .deb and .tar.gz., and then a 10.1 rc4. Any recommendations?

The ".deb" is an installer file type for Debian (Ubuntu). The ".tar.gz." is like a zip file container. "10.1 rc4" is the newer unreleased version, but it may include hardware support for some cards. I would start with the ".deb" file if the Ubuntu software center version doesn't work.

---

