---
title: "Complete System Lockup Freeze with Ipod"
date: 2008-05-19
forum: Multimedia Software
---

### Post by mocha on 2008-05-19
I was curious if anyone else has or had this problem and what it might mean.  Sometimes when I have my 5th gen Ipod connected and transferring files to it with gtkpod it will cause the entire system to completely freeze.  It freezes so hard that the computer reset button doesn't work, neither do the Alt-SysRq keys.  The only way out is to hold down the computer power button on my box.  I am trying to figure out if this is an issue with Hardy or if my Ipod is dying.  I have to do a "sudo fsck.vfat -a /dev/sdxx" whenever this happens in order to fix the corruption that occurs on the Ipod when the system goes down.  Prior to these problems I was using the same Ipod with Feisty and never had any system freezes or any other problems.  I don't know if this is just a coincidence or not.  When the system freezes there is nothing in the system logs after rebooting.  Is there some debugging I could do during the file transfers?  Thanks for any comments.

I should also point out that the system doesn't freeze everytime I transfer files, just most of the time.  For example, this evening I was transferring quite a large amount of music and videos (about 6 GB worth) and my Ipod was going to have about 1.5 GB leftover after the transfer.  During the transfer the system freeze occurred.  I rebooted and did fsck.vfat on the Ipod, remounted it, used gtkpod's "check files" function, then resumed to transfer the files that never made it or got corrupted the first time.  It worked the second time around, no problems.

There was another occurrance when I simply plugged the Ipod into the USB port and the system froze.  This only happened once.

---

