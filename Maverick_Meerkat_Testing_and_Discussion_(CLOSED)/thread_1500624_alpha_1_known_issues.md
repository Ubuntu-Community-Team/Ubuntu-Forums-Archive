---
title: "alpha 1 known issues"
date: 2010-06-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jppr on 2010-06-03
From [https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview](https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview):

> **Known issues**

As is to be expected at this  stage of the release process, there are several known bugs that users  are likely to run into with Maverick Alpha 1. We have documented them  here for your convenience along with any known workarounds, so that you  don't need to spend time reporting these bugs again:  

[LIST]
[*]Ubuntu Netbook launcher (both the 2D and 3D variants)  have an empty "Favourites" tab. Please switch to the "System" tab to  find the launcher for the installer. Due to the same root cause, the  panel configuration looks like in standard GNOME instead of the UNE  specific setup. ([588675]("https://bugs.launchpad.net/bugs/588675"))
[*]On the alternate images, the boot menu's  "Rescue Mode" item shows as "Alternative desktop environments". ([588221]("https://bugs.launchpad.net/bugs/588221"))
[*]The Ubuntu Server amd64 CD image is oversized and will  not fit onto a standard 700MB CD. However, you may still test it using a  DVD, a USB drive, or a virtual machine. ([587893]("https://bugs.launchpad.net/bugs/587893"))
[*]Encrypted home directory creation may be  broken on some images. ([588705]("https://bugs.launchpad.net/bugs/588705"))
[*]The Audio and Video tasks are  uninstallable on Ubuntu Studio images. You may install most of the  packages they contain with a package management tool after installation;  bitscope, mencoder,  and mplayer are currently broken. ([588780]("https://bugs.launchpad.net/bugs/588780"))
[*]When installing Xubuntu, the systray appears in the  middle of the screen, with three icons flashing constantly. This  prevents the installation from the live environment, and makes the  desktop pretty much unusable after any installation completes. There is a  workaround to this issue described in the bug report. ([586012]("https://bugs.launchpad.net/bugs/586012"))
[/LIST]


---

### Post by 23meg on 2010-06-03
Note that the /$RELEASE/TechnicalOverview wiki pages are working copies for the technical overview of each milestone release (which means they're not meant to be final), and Alpha 1 has not yet been released as of this moment.

---

### Post by ranch hand on 2010-06-03
The main known issue with 10.10-testing is that it is in development and therefore will break.

That is what makes it FUN.

---

