---
title: "Wireless dies after update"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by rtlinux on 2009-02-07
Hello everyone.

I recently installed Ubuntu 8.10 on my laptop.  I configured my wireless using network configuration, and when I restarted it worked great.  My problem came when I updated using the update manager.  After updating and rebooting, the wireless doesn't connect or even show up on the top bar.  I know the kernel was 2.6.27-7 before the update and now is 2.6.27-11.  I finally gave up and reinstalled ubuntu from the live cd again.  Once again the wireless worked fine, but I am afraid to update because it might kill the wireless again.  Is there a way to find out which update caused the problem, or could it be the kernel itself?  There were 245 updates, so I have no idea which one did it.

My laptop is a Gateway model TA7 and the wireless card is the Intel 3945abg. Thanks!

---

### Post by odium1 on 2009-02-07
just look and see which update is for kernal 2.6.27-11 i suppose. that's what i'm going to do. i updated a few nights ago as soon as the update was available and now my wired (eth0) connection doesn't work unless i boot into the previous kernel and even after that it's ridiculously slow. i've been reading around for a few days now trying to figure out a good solution and all i can tell you is the bug was reported (several times) on launchpad and the developers are on top of it. I'm sure they'll have a fix for it before long. Until then we just have to make do and ride it out. just look for the newest kernel update and un-check it.

---

### Post by ugm6hr on 2009-02-07
Look here: [http://ubuntuforums.org/showthread.php?p=6663910#post6663910](http://ubuntuforums.org/showthread.php?p=6663910#post6663910)

Might give you ideas...

---

### Post by rtlinux on 2009-02-07
I'll try unchecking the kernel updates and see how that goes.  I think are four or five updates that mention the new kernel, so I'll try updating without them.  If I figure anything out I'll repost.  Thanks again!

---

### Post by rtlinux on 2009-02-07
***Update***

I update everything except the packages that mentioned the new kernel. My wireless still works so it must be a kernel problem. I'm just happy to have my wireless working.  Ubuntu is the only distro I've tried so far that I've been able to connect with.:D

---

