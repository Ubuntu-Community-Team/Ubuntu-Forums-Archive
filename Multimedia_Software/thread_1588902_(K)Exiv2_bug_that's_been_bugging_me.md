---
title: "(K)Exiv2 bug that's been bugging me"
date: 2010-10-05
forum: Multimedia Software
---

### Post by KungFuJesus on 2010-10-05
Ok so I'm not normally one to gripe about problems in a given open source project if no solution is found yet.  However...this bug has been in existence since 10.04's launch and is making image imports from my Nikon Camera impossible.  The fix for it came out not long after the bug was reported for the upstream projects, and I filed a bug many many months ago on launchpad only to have it ignored by the project.  

The Exiv2 Nikon makernote bug was "triaged" forever ago with nobody stepping up to the plate.  The solution simply requires somebody to update Exiv2 to .21 and then update dependent packages (in this case the kdegraphics package).  The fact that Maverick Meerkat doesn't even have these fixes yet is very disappointing and is making me stray further and further away from the Ubuntu project as they lag so far behind.  I don't mind using older stable versions as long as they don't have usability issues, but this is definitely a big show stopper for me.  This combined with recent regressions I've been having with the gutenprint packages in Ubuntu with my Epson stylus and brother laser print both have my quite frustrated.  But my main frustration is the fact that this isn't fixed yet:

[https://bugs.launchpad.net/ubuntu/+source/exiv2/+bug/596327](https://bugs.launchpad.net/ubuntu/+source/exiv2/+bug/596327)

---

### Post by KungFuJesus on 2010-10-10
Post Maverick this issue still present, how can I find the maintainer of the KDE Graphics package?

---

