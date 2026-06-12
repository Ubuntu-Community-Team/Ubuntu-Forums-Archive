---
title: "ATI 4870 + Xinerama + 3D Possible?"
date: 2009-10-22
forum: Multimedia Software
---

### Post by CraigWatson on 2009-10-22
After trying Karmic in VirtualBox, I'm very impressed, and considering changing the Fedora section of my tri-boot setup (Win7+Vista+Fedora) to Ubuntu.

The killer question for me is 3D support. I've had to put up with buggy and/or non-existent 3D support in Fedora for a while because of my dual-monitor setup in Xinerama (the only way I've got it to work properly) using the RadeonHD drivers.

If anyone knows of a way to get this working in Ubuntu, or any guides that would help, it would be appreciated. 3D support is pretty much the only thing stopping me from going 100% Penguin, so it's quite frustrating!

Cheers,
Craig :D

---

### Post by markbuntu on 2009-10-22
Xinerama is in the process of being deprecated as RandR gains funtionality. One function missing from current RandR versions is multiple gpu support which xinerama does support, but not with compositing (3D).

Good news though, multi gpu support has been put back into RandR for the next release so this should allow mulitple gpus with compositing (3D). Unfortunately for you, there is only rudimentary (not working) 3D support for the R700 series ati cards in the RadeonHD driver but this should be changing in the next few months or so which is also about when the new RandR will be making its way into the distros.

Have you tried a recent proprietary fglrx driver with that card?

---

### Post by CraigWatson on 2009-10-26
I haven't really tried a lot since Fedora 10 was released (I did an in-place upgrade from F10 to F11) as I'm more concerned with getting a stable system than I am with playing with drivers.

It seems F12 is a bit more advanced and the RPMFusion Catalyst drivers are reportedly pretty decent so I'll give those a try with the F12 beta :)

---

