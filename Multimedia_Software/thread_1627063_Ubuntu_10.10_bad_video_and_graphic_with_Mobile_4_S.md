---
title: "Ubuntu 10.10 bad video and graphic with Mobile 4 Series Chipset Integrated Graphics"
date: 2010-11-21
forum: Multimedia Software
---

### Post by naymin on 2010-11-21
Hi,

I'm having problems on my Fujitsu Lifebook A-1110 with video play back (repeating played frames like every 10 or 15 min intervals, like it rewinds to last 2 seconds, played it for a while and skips it back to current frame again. Sorry that couldn't clarify any further.) and 3D games (like GLEST and HoN).

I did some googling and I came up with this site intellinuxgraphics.org which provide open graphic drivers for intel. "sudo lshw" says my VGA controller is using a driver called i915. I managed to install those open drivers, both 2D and 3D. But it says that i might need to change xorg.conf > device section to use "intel" or something like  that. But in maverick, the config files are scattered in etc/X11/xorg.conf.d folder. I looked through every file and couldn't find any section named "device". I was hoping this driver would probably solve the problem. Can someone tell me where the device config is?

Yes, I also looked through proprietary drivers for linux from IEGD. But it doesn't seem to support the kernal that maverick is using. So I gave it up.

Apart from VGA, everything else works great! Am I doing it the right way in solving this problem? Is there any better way? Or is there no way at all? If it's so then, I'll have to live with it for a while. I do plan to get a new Ubuntu certified dell laptop (possible Vostro V13 or 3300). Can anyone recommand any good dell laptop for Ubuntu?

Sorry for putting up a lot of questions.

Best Regards,
Nay Min

---

