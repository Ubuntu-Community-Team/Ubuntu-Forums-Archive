---
title: "O2 Mobile Broadband - Anyone have it working in Karmic?"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by bobnutfield on 2009-11-12
Hi Everyone,

I read all the other threads about the Huwawi E620 mobile dongle, but I haven't been able to get it working.  I have Ubuntu installed on three computers (Desktop, Acer Aspire One netbook and Toshiba laptop.)  The dongle dosen't even show up (except in lsusb) no necessary tty ports are created.  But, the funny thing is that I have Fedora 10 also on the laptop and the modem shows up and connects right away with no configuration at all necessary.

My question is: does anyone know if there is an issue with the 2.6.31 kernel with mobile broadand?  Fedora 10 uses 2.6.27 and I have read in other posts that some have been successful getting connected by downgrading the kernel.  I would have thought that Karmic would have nailed mobile broadband down by now.

Anyone have any ideas how to fix this?

Thanks in advance for any replies.

---

### Post by pdc on 2009-11-12
Yes; there seems to be a problem; as those moving from a working 9.04 with 3G modems report they do not work on 9.10

this bug 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

covers the issues, and suggests karmic updates will fix 

however this post

[http://ubuntuforums.org/showthread.php?t=1305931&page=4](http://ubuntuforums.org/showthread.php?t=1305931&page=4)

(post #36) disagrees

stay with 9.04

(as an admin commented: if it ain't broke, leave it alone)

by the way: what are the various kernel versions for your various distros: particularly, fedora ?

---

### Post by bobnutfield on 2009-11-12
> **pdc said:**
> Yes; there seems to be a problem; as those moving from a working 9.04 with 3G modems report they do not work on 9.10

this bug 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446146)

covers the issues, and suggests karmic updates will fix 

however this post

[http://ubuntuforums.org/showthread.php?t=1305931&page=4](http://ubuntuforums.org/showthread.php?t=1305931&page=4)

(post #36) disagrees

stay with 9.04

(as an admin commented: if it ain't broke, leave it alone)

by the way: what are the various kernel versions for your various distros: particularly, fedora ?

Thanks for that information, but I have already upgraded all three computers so I will have to hope that a fix will in fact come in a future update.

For your other question, I use Fedora 10 and Slackware-current triple booted on the Toshiba laptop.  I stayed with Fedora 10 so that I could continue to use the fglrx ATI driver until it is no longer supported in February next year.  It uses the 2.6.27 kernel, Fedora 11 uses 2.6.29 and Fedora 12 (still in testing) will use 2.6.32.  Slackware is on 2.6.29 for Slackware 13, but it is an extremely flexible distro and most any recent kernel will work with it without too much issue.

Obviously, I have a netbook so that I do not have to carry a large laptop around, but that is what I got the 3G modem for, and it is going to be a hassle to work.

Thanks again

---

