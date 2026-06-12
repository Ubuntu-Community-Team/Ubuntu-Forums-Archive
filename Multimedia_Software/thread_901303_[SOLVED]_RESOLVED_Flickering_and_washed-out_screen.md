---
title: "[SOLVED] RESOLVED: Flickering and washed-out screen for Twinhead e10 (Geode LX Video)"
date: 2008-08-26
forum: Multimedia Software
---

### Post by phpmonkey on 2008-08-26
Just thought I'd share this fix.

The problem doesn't occur for versions before 8.10
I found the fix here:

[https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/237186](https://bugs.launchpad.net/ubuntu/+source/module-init-tools/+bug/237186)

It's a problem with module-init-tools & the blacklist

You just need to download the .deb file here [https://launchpad.net/ubuntu/intrepid/i386/module-init-tools/3.3-pre11-4ubuntu9](https://launchpad.net/ubuntu/intrepid/i386/module-init-tools/3.3-pre11-4ubuntu9) (I've also put it as an attachment) and install it, using gDebi package installer for example (It'll tell you there is an older version in the software repository. Proceed anyway).

And voila! Upon reboot no more issues! :-({|=

---

### Post by Oldsoldier2003 on 2008-08-27
Marking this post as solved to help searchers. This reply is to untag the post for the Unanswered Posts Team

---

### Post by phpmonkey on 2010-10-12
Just an update - this has not been a problem on this computer for lucid & Maverick :KS

---

