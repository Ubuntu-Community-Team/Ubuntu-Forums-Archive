---
title: "Applications can't see network"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by ibexslam on 2009-01-17
From the file browser, we can see other users on our mostly-windows network.  But, when opening files on our new intrepid installation, the network does not show up.

Did some research, and found that the solution involves a thing called FuseSmb.

Followed the instructions on this page:
[http://ubuntuforums.org/showthread.php?t=525736](http://ubuntuforums.org/showthread.php?t=525736)

One difference: did not see the option in intrepid to "tag 'allow use of fusesmb'", so "Mount user-space filesystems (FUSE)" was checked instead.  (That's the same thing...isn't it?)

After rebooting, the network was still not visible from within applications.  I noticed that "Mount user-space filesystems (FUSE)" for root was unchecked again, so I re-checked it.  Hmm.

Then I manually entered the command: fusesmb /media/network (with a sudo) in the terminal.  

After this, the network was visible from an application where it wasn't visible before.  However, when I tried to select it, I got a "Permission denied".

Aaargh!  Can someone help me hack my way out of this thicket?

I.

---

### Post by ibexslam on 2009-01-19
Any help at all will be appreciated.

I.

---

