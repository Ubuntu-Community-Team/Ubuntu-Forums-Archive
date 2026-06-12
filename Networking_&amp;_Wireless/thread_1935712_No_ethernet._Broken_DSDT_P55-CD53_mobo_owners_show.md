---
title: "No ethernet. Broken DSDT? P55-CD53 mobo owners show yourself!"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by Saorex on 2012-03-04
Hi guys. To make a long story short, during some hackintosh build tests, I installed a DSDT for the wrong bios version on my MSI P55-CD53 mobo. As a result, the integrated Realtek 8111DL doesn't work anymore, no matter what OS I boot with (Ubuntu, Mac OS X, Windows 7).

I updated the mobo's bios to the latest version (1.B), but it didn't help. At this this, I think my only solution is to find someone with the same mobo and as him a copy of his own DSDT.

So if you own a P55-CD53, please say so!

OR

If you have any idea to fix the problem without buying an ethernet adapter, I'd be very grateful.

Thanks for your help.

---

### Post by Saorex on 2012-03-04
Fixed!

I'm "sorry" to say the problem was not DSDT-related. I realized (reading other forums) that a network adapter could into "deep sleep mode". And that's what happened. I did a CMOS reset and now it's back online.

I disabled Mac OS X's sleep mode, so I suppose it won't happen again. Most hackintoshs have sleep problems...

Thanks anyway for those of you who took the time to read.

---

