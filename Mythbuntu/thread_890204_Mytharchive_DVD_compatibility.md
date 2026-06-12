---
title: "Mytharchive DVD compatibility"
date: 2008-08-14
forum: Mythbuntu
---

### Post by RickThorpe2006 on 2008-08-14
I used to be able to create a double-layer DVD iso from Mythtv on my backend machine, transfer the iso up to my iMac and burn on a DVD+R DL, and the resulting DVD would play without problems on any of my players.  After a couple of months of not using this function, I have started to try to use it again.  The iso burns onto the DVD fine, but then the DVD is not recognized as a supported format by the iMac or any DVD player -- BUT is recognized by my Ubuntu laptop.  If I then use Wine to run DVDShrink, compress the menus (but not the main title) to 99%, and burn the resulting iso to DVD, it works on all my machines.  Any ideas as to what could be done to avoid the extra step of running mythburn.iso through DVDShrink before burning?

---

### Post by Timuntu on 2008-08-23
I think this from a bug in genisoimage.

[https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942]("https://bugs.launchpad.net/ubuntu/+source/cdrkit/+bug/233942")

[http://ubuntuforums.org/showthread.php?t=787299&highlight=genisoimage]("http://ubuntuforums.org/showthread.php?t=787299&highlight=genisoimage")

Taking out the "--dvd-video" options in the mytharchive script or down grading to a previous version of genisoimage seems to work for me to get the DVD readable in windows XP.

---

