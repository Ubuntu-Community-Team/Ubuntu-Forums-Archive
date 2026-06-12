---
title: "ipod &quot;Invalid Extent Entry&quot;"
date: 2010-11-15
forum: Multimedia Software
---

### Post by thompson20 on 2010-11-15
Hey,
I have an 80gb iPod Classic which I originally used with my iMac three years ago. I no longer have that computer, and I'm now running Ubuntu 10.04 on a Dell Mini 10v. I had been using gtkpod to add music (took a while to get it to work, had to borrow a friend's laptop to disable journaling) but now my iPod has become read-only. (I suspect an accidental unplugging.) 

Previously, fsck.hfsplus would fix the read-only problem but now it's telling me:

sudo fsck.hfsplus /dev/sdc2
** /dev/sdc2
** Checking HFS Plus volume.
   Invalid extent entry
( 6, 155906998 )
** Volume check failed.

Anything I can do? I no longer have the original library and would like to keep all of my play counts and ratings. I know gtkpod can copy all of that to my hard drive, but unfortunately it often quits unexpectedly when doing so. As a last resort I will try that method, but I was hoping to just repair the disk.

Thanks,
Thomas

---

