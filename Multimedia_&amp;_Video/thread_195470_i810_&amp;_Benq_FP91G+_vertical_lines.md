---
title: "i810 &amp; Benq FP91G+ vertical lines"
date: 2006-06-12
forum: Multimedia &amp; Video
---

### Post by botchka on 2006-06-12
Greetings all.

I stepped through:

dpkg-reconfigure xserver-xorg

to configure my i810 graphics chip on this older Compaq I have laying around.  However, at the default resolution and my monitor's native resolution of 1280x1024, there are vertical blue lines.  I've changed the refresh rate and that hasn't helped.  The highest resolution that is viewable with no vertical lines, is 1024x768.  This is not my monitors native resolution so the text isn't as sharp as I'd like.

I can post my xorg.conf is someone thinks that will help.  Any help is greatly appreciated.

GregD

---

### Post by fentruk on 2006-06-13
I have the same problem on an old 933MHz Compaq P3. I was able to get it working correctly by changing the "DefaultDepth" option in my xorg.conf to 16 rather than 24. 

This also had the side effect of allowing DRI to be enabled. I would rather have 24 bit color though, as I almost never use 3d features on this old box. If anyone has another soultion it would be good to hear it.

Hope that helps in the meantime.

---

