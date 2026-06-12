---
title: "Added step in HOW-TO:ATI why?"
date: 2006-03-01
forum: Multimedia &amp; Video
---

### Post by otetiani on 2006-03-01
I performed the steps as written in this HOW-TO : [http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")

What happened when I rebooted the final time was I got an error and xwindows wouldn't open.  After messing around I figured I'd reperform the steps.

When I got to the step: sudo ./ati-driver-installer-8.22.5-i385.run --buildpkg Ubuntu/breezy

I noticed it unpacked the .deb package fglrx-sources_8.22.5-1_i386.deb

This is not in the next step to sudo dpkg, but I added a step:

sudo dpkg -i fglrx-sources_8.22.5-1_i386.deb

Long story short this worked - why???

I am pretty new to linux, so I may have messed something up doing this, but it worked.

---

### Post by Des33 on 2006-03-01
> sudo ./ati-driver-installer-8.22.5-i385.run --buildpkg Ubuntu/breezy

creates 5 .deb packages for me

---

### Post by otetiani on 2006-03-01
hmmm... I only saw the 4 as listed below:

fglrx-sources_8.22.5-1_i386.deb

xorg-driver-fglrx_8.22.5-1_i386.deb

fglrx-control_8.22.5-1_i386.deb

fglrx-kernel-source_8.22.5-1_i386.deb

What was the 5th?  And do you know why fglrx-sources and this 5th were not included in the dpkg -i step but the other 3 were?:???:

---

