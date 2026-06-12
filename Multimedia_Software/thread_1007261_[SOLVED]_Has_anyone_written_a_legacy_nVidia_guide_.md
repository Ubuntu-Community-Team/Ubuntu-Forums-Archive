---
title: "[SOLVED] Has anyone written a legacy nVidia guide yet?"
date: 2008-12-10
forum: Multimedia Software
---

### Post by dawynn on 2008-12-10
With all the issues that we've seen with the legacy nVidia drivers, has anyone in the know written a comprehensive guide, showing how to fix the known fixable problems (in proper Ubuntu ways), and identifying what still needs a fix?

Problem that I've had is that the answers are scattered in some very *very* very lengthy bugs.  And then its not always precisely clear whether or not *I* need to apply each fix.  And, for that matter, what's fixed with the 96 series, that may not be fixed with the older series (72?).  And even those fixes that exist do not always use the proper tools (hand-editing xorg.conf instead of using nvidia-xconfig).

If I need to create such a document, I'll give it a shot, but if someone else has already done the legwork, it would save me a lot of time, and frustration.  I personally still can't get glxgears to work.

Basically, we'd need a guide that would enumerate:
1) Status of latest drivers (still in proposed?  or have these advanced to the main repositories?).
2) How to fix wine fonts (solution is available and works, for 96 at least).
3) How to fix Open Office menus (haven't had this problem personally, so I don't know the status).
4) How to get glxgears working (solution may be available, but I haven't found it yet).
5) How to get compiz working (I'm afraid to even try compiz on my old machine).
6) Any other known issues that I'm forgetting at this point.

---

### Post by sirgimp on 2008-12-10
I tried intalling Ubuntu 8.10 on a friend's computer. He had a nvidia graphics card. We couldn't get Open Office menus to work. Eventually we gave up and deleted Ubuntu, reinstalled Windows and Open Office and everything works find. I would love to get more info on this Open Office bug with nvidia cards and drivers.

---

### Post by dawynn on 2008-12-11
I started this other thread intended to be a summary of real fixes:
[http://ubuntuforums.org/showthread.php?t=1008787](http://ubuntuforums.org/showthread.php?t=1008787)

Meanwhile, if anyone stumbles on this and can help me, please review the attached files.

Basically -- I have basic video, but have no glx.  Glxgears shows a black screen and quickly aborts.  Any idea of what to try here?

---

### Post by dawynn on 2008-12-16
NM.  I simplified my xorg.conf.  Automated tools are nice, but the automated tools had added extra configurations that were, honestly, confusing the X system.  So, I went through and intelligently configured just one screen, just one monitor, just one device, with appropriate selections from the two configurations for each item that were out there.

A reboot and glxgears was working fine.  Crack-Attack and Neverwinter Nights worked fine also.  A little more work learning how to temporarily shut off pulse-audio, and pSX was ready to go too.  I'm back in business.

---

