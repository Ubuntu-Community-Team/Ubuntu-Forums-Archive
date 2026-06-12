---
title: "Cannot drill down through file system"
date: 2010-05-30
forum: Mythbuntu
---

### Post by chipppy on 2010-05-30
Good Evening

I have an odd problem since upgrade from 9.10 -10.04

I lost any auto mount of things that connect via a cable.
Ethernet not working when plugged in
        I found a permission to auto-connect unticked. This one is fixed

No longer auto mount USB devices
        I can see Ssdc1 (usb device) via mount manager but unable to mount it, 

Strangest of all I cannot drill down through file system in Thunar, when started from desktop.  eg drill down to copy in a new movie from usb stick.  I can drill into /var and thats it.  When I double click on /var/lib nothing happens.
Strangely when I go through a terminal and use sudo thunar I can not only drilling through the file system like normal but my USB stick auto mounts into the files system link normal.

I feel that my problem is a permission problem (something has changed in the permissions somewhere) but I cannot for the life of me find where the change has occurred and therefore where to fix the problem.

In Thunar under preferences all the auto-mount boxes are ticked as per normal.

Any suggestions on where to look to fix my automount and file system drill down problem?? 

Cheers
chipppy

---

### Post by drs305 on 2010-05-30
> **chipppy said:**
> 
Strangest of all I cannot drill down through file system in Thunar, when started from desktop.  eg drill down to copy in a new movie from usb stick.  I can drill into /var and thats it.  When I double click on /var/lib nothing happens.
Strangely when I go through a terminal and use sudo thunar I can not only drilling through the file system like normal but my USB stick auto mounts into the files system link normal.


This has been a frustrating thing for me, since I use pcmanfm for my 'root' browsing. There is a bug which affects pcmanfm and the default file browser for Xubuntu. I reported it long ago in Ubuntu but at the time didn't realize how much more important it was in Xubuntu.

At any rate, if you use a view other than "Detailed list" I believe you will find that you can drill down the folder structure without difficulty. The problem is related only to the detailed view, and there has already been a fix for Xubuntu, although it may still be in the "proposed" repository.

Here is a bug report link, which also includes some ppa's with the fix should it not be available to you through the normal repositories quite yet:
[https://bugs.launchpad.net/ubuntu/+source/exo/+bug/520118]("https://bugs.launchpad.net/ubuntu/+source/exo/+bug/520118")

I'm waiting for it to make it into the normal Ubuntu repositories and will be very happy when it does.

---

