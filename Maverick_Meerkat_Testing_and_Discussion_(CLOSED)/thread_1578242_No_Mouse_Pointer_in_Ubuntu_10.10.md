---
title: "No Mouse Pointer in Ubuntu 10.10"
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by arjunbajaj on 2010-09-20
Hey,

I am using IBM R51, and i think there's a huge bug in ubuntu 10.10 beta....

There is no mouse pointer...

The **Mouse Pointer doesn't show up**... But i can hover to something like the shutdown button with my mouse....

**Can You tell me is there any fix for that????**

 So i can use... and i hope this bug is not there in 10.10 final release... My laptop also had problem running 10.04....but i hope from 9.04 i could switch to 10.10 by doing a fresh install.....

thnx...

---

### Post by roncville on 2010-09-20
I had the same problem with my R51, and the Beta release.  The problem went away with some update between then and now.  Just be sure xorg.conf is removed so you get the default video driver (fbdev).

---

### Post by TKbuntu on 2010-09-20
> **arjunbajaj said:**
> Hey,

I am using IBM R51, and i think there's a huge bug in ubuntu 10.10 beta....

There is no mouse pointer...

The **Mouse Pointer doesn't show up**... But i can hover to something like the shutdown button with my mouse....

**Can You tell me is there any fix for that????**

 So i can use... and i hope this bug is not there in 10.10 final release... My laptop also had problem running 10.04....but i hope from 9.04 i could switch to 10.10 by doing a fresh install.....

thnx...
The 'invisible mouse pointer' bug has been fixed.  The fix is in effect when you sudo apt-get update and sudo apt-get upgrade.


Information concerning this bug maybe found here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/614176)

Concerning your earlier post, I have an IBM Thinkpad R51.  This pc was affected by the Lucid 'i855 freeze'.  However, except for the mouse bug, the R51 plays well with Maverick.

Regards,

Tony

---

### Post by arjunbajaj on 2010-09-21
Hey guys.... thanks for your replies...

i'll switch to 10.10 beta as soon as my other computer starts working because i dont want to take a risk in loosing both the computers for a day....

by the way can i take the risk of switching over to 10.10 beta....
cause you also hv R51's so does it give any problem to you while your using?????

thnx...
and thnx a lot for answering....

---

### Post by TKbuntu on 2010-09-22
@ arjunbajaj : Well, as I mentioned, I am able to use a Thinkpad R51 (2 Maverick partitions).  Other than the temporary invisible mouse pointer bug (which was due to an upstream kernel mod, not Maverick devs), I have no open issues at this time.

However, please understand that any Beta software is to be used for testing purposes only.  Expect it not to be stable and even to break at times.  I imagine you know this, Beta software is not suitable for production use.

Have you considered using the Live Cd, or putting Maverick on a separate partition?  Be sure to use the recent ISO (one that has the mouse bug fix).

Regards,

Tony

---

### Post by arjunbajaj on 2010-09-23
Hey Thanks Tony for your reply. But there's one problem.
I tried to install Ubuntu 10.10 on a partition but it didn't install. Can you tell me does Ubuntu 10.04 work well on IBM R51???
Because the last time i did a few months back it didn't work pretty well...

**If there's a way to install Ubuntu 10.04 for the time being on my laptop till Ubuntu 10.10 releases, I would be happy to install it...**

Thanks.... Please Reply

---

### Post by ward83 on 2010-09-23
I had the same problem after upgrading my laptop to 10.10 beta. For me, the workaround was to comment out the video driver line in xorg.conf. It was using the "intel" driver provided by xserver-xorg-video-intel.

This is on a Gateway MX6030, with intel 8xx video card.

---

### Post by TKbuntu on 2010-09-24
> **arjunbajaj said:**
> Hey Thanks Tony for your reply. But there's one problem.
I tried to install Ubuntu 10.10 on a partition but it didn't install. Can you tell me does Ubuntu 10.04 work well on IBM R51???
Because the last time i did a few months back it didn't work pretty well...

**If there's a way to install Ubuntu 10.04 for the time being on my laptop till Ubuntu 10.10 releases, I would be happy to install it...**

Thanks.... Please Reply
@arjunbajaj - As of today, I am not able to boot Lucid 10.04.1 (desktop live-cd dated 18 August 2010) on my IBM Thinkpad R51.  FYI, (lspci | grep VGA)

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Information is available on the web describing various workarounds for the Lucid i855 freeze 'bug/feature'.  However, the outcome seems to depend on exactly which card you have, etc.

Unless you have time, energy, patience, etc, I would recommend to stay away from Lucid 10.04.1.

Maverick 10.10 should go Live in about two weeks.  Why not run the desktop live-cd until the Maverick Beta ends, and then install if you are having success with the live-cd?

Of course I am in no position to guarantee that you will have no issues if you install Maverick (Beta or post Beta), so please proceed with caution.

FYI, I am able to boot using the Lucid 10.04.1 desktop live-cd on a Lenovo (i386) and an Inspiron (amd64).  Both cases seem to work OK (can connect wireless and surf).

Regards,

Tony

---

