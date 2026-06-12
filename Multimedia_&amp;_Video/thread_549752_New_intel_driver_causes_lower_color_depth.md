---
title: "New intel driver causes lower color depth??"
date: 2007-09-13
forum: Multimedia &amp; Video
---

### Post by ghstzr0 on 2007-09-13
I have a small but vexing problem; here's the situation...

I recently purchased the DELL 1420 N pre-loaded with Ubuntu 7.04.  The hibernate feature was not as stable as I wanted it to be (it didn't always come back from a hibernate).  So, to fix this, I install uswsusp and the s2disk feature worked great except for the fact that 915resolution would not be reloaded upon resume.  So THEN I installed xserver-xorg-video-intel and am now using the new o-s intel driver (my notebook has the intel GMA X3100 chip).  Everything works great EXECPT...

My X-server seems to be loading with a color depth lower than before...

BEFORE YOU ASK:  My xorg.conf file WAS NOT CHANGED other than to change "i810" to "intel".  It still has all the color depths (up to 24) listed under the correct section and the DefaultcolorDepth is STILL 24.

Any Ideas???

---

