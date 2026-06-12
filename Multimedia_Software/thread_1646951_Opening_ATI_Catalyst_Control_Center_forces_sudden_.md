---
title: "Opening ATI Catalyst Control Center forces sudden logout?"
date: 2010-12-16
forum: Multimedia Software
---

### Post by FullAuto on 2010-12-16
Ubuntu 10.10 x64. Got a second monitor and enabled Xinerama. It asked me to restart, I did. I opened ATI Catalyst Control Center after the restart and saw the control panel window open for about half a second before suddenly finding myself at the login screen.

ATI Catalyst Control Center has always seemed to work fine up until I enabled Xinerama. I tried removing the ATI driver, restarting, re-enabling it, restarting, and ATI Catalyst Control Center worked fine again. But, as soon as I enabled Xinerama it went back to logging me out whenever I tried to open the control center. I've tried from the GUI menu as well as the terminal using 'gksudo amdcccle', same result every time.

The dual monitor functionality seems fine, but I need to get back into the control center to adjust the colors. I do a lot of photo editing, and the adjustments in the control center really is a great tool to let me get the colors how I'd like.

It's probably obvious, but yeah, I'm a Linux n00b trying to escape Windows.

---

### Post by HeirPixel on 2010-12-16
Wow, I was just searching for an answer to the same problem! It's bad enough that Xinerama won't work with compositing, but now I can even adjust any of my settings....

---

### Post by dsjstc on 2010-12-16
Similar-sounding issues here, still unresolved.  Please post if you solve this.

Have you had any luck with the open source radeon driver and Xinerama?

---

### Post by dsjstc on 2010-12-16
If it was the same issue as mine, it's a bug.
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539)


Solved by updating xserver-xorg-core and xserver-common from PPA:
[https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539](https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539)

---

### Post by FullAuto on 2010-12-16
> **dsjstc said:**
> If it was the same issue as mine, it's a bug.
[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539)


Solved by updating xserver-xorg-core and xserver-common from PPA:
[https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539](https://launchpad.net/~jared-bunting/+archive/xorg-xserver-650539)

Amazing, thanks!

I installed the fix, and then tried opening the control center again. It did log out one more time, but once I logged back in it opened correctly. Looks like it's fixed:D

---

### Post by HeirPixel on 2010-12-18
Brilliant, fixed it for me too! I had just noticed the same issue with Skype when I read to bug in LaunchPad. Glad to know the community is so thorough!

---

