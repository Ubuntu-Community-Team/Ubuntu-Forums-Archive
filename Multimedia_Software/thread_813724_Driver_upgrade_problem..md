---
title: "Driver upgrade problem."
date: 2008-05-31
forum: Multimedia Software
---

### Post by Silent Warrior on 2008-05-31
First things first, I can probably do with reformatting the root-partition... Clean slates an all that. But I'd rather solve this problem good and proper.

Now, ATI drivers. Yummy. I've been dutifully installing the proprietary drivers, as per normal Windows procedures (don't ask me why...), and lately tried the open-source repository variant. And now I've stepped on a bona fide complication. When I update the drivers, I try to build packages first - which hasn't been working this year except for 8.4, so I've most frequently fallen back to ATI's installer.
So now that 8.5 is out and they refuse to be built into .debs (--buildpkg Ubuntu/8.04), I thought removing the packages by way of Synaptic might be a suitable step, before going Installer UI. Besides the driver-package it worked like expected... DUMP:
```
Removing xorg-driver-fglrx ...
dpkg-divert: mixup(?*) in divert-to
  at removal of "diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx"
  found "diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx"
```
(Which results in an "error code 2" in the "post-removal script".)
*Translated from Swedish. The actual word on screen is 'sammanblandning'. If anyone wants to try their own hand at translating that, do go ahead.

Note that the proverbial rub seems to be that the existing file lacks the requested .2 in the filename. :confused: It r w3rd.

This has the added effect that I can't do anything with package-managers until this matter is solved - this package is always first on dpkg's todo-list. In Synaptic, I can't select anything else than 'Deselect' and 'Select for complete removal' (purge remove) - ordinary 'Removal' is set by default.

How do I make this computer play nice again?
(I'm sort of skeptical about these drivers, though. In the Windows-version I can't play any OpenGL-games, whereas 8.4... well, sort of works. I can fully load things before I need to worry about crashes, at least.)

I forgot to mention that this computer runs on AMD64 8.04. The card (though possibly irrelevant) is a Radeon X1900XT.

... Do I hear an idea that's less trouble than reformat + reinstall? Anyone at all?

---

### Post by yaMan on 2008-05-31
I had the same issue.  Try doing this:  Go to Synaptic Package Manger and search for the xorg-driver-fglrx package.  Select the package and then go to "Package" -> "Force Version".  It will then ask what version you want to downgrade to.  I selected the latest one.  Then click Apply.  That will downgrade the package to a supported version.  Once that was installed I selected all the other packages needed for the driver (fglrx-amdcccle, fglrx-kernel-source, and xorg-driver-fglrx-dev).  This will take your drive to version 8.4.

I think I'll wait to upgrade to 8.5 for a while.

---

### Post by Silent Warrior on 2008-06-01
Ya-HA! Fix0red!

(Though this actually had me downgrade to 8.3 - I had 8.4 installed. 8.3 is a keeper.)

---

