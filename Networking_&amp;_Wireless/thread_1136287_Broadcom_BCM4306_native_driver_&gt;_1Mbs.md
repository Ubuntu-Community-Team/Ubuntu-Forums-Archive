---
title: "Broadcom BCM4306 native driver &gt; 1Mb/s"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by DouglasK on 2009-04-24
If you're running a Broadcom BCM4306 card, which uses the b43legacy kernel driver, you've probably noticed that the driver does work, but only at 1 or 2 Mb/s.

As of Kernel 2.6.26, a patch was included to fix this limitation in the upstream kernel at linux.org.

Unfortunately this patch has as yet not made it into the 2.6.28 kernel distributed with Jaunty Jackalope (9.04).  The [patch]("http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-10/msg07179.html") is mentioned in the [official bug base]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/201225").

If you're comfortable with the command line and compiling packages from source, the fix is to install a custom kernel from the linux.org source.   You don't need to apply any patches to the generic source, just follow the howto in the post at the bottom of this message.

If you're NOT comfortable with the command line and compiling packages from source, I'd wait on installing anything.  

FOLLOW THE HOWTO CAREFULLY.  BACK EVERYTHING UP FIRST.  If you fsck it up badly enough you can seriously trash your file system and data.  Again, back up all data.  

Proceed at your own risk.

Without further ado, the "Master Kernel Thread":
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

~~Douglas K

---

