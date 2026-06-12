---
title: "bcm4309 with ndis or fwcutter now works flawlessly"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by Casey on 2006-06-25
I've managed to figure out my (and maybe other's problems) with the bcm4309 adapters.  This fix may also apply to bcm4306 issues that some are having.

This was tested on a Dell Latitude D800.

Symptoms: The wireless drivers were locking up at boot (sometimes).  This may be related to what some people had reported about having to boot to windows before using wireless.  This was true with both ndiswrapper (using the drivers found here: ([http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")) which work flawlessly otherwise and the bcmwl-fwcutter which also work flawlessly (and are described in the broadcom howto).

Testing: Changing ANY option in the BIOS was able to prevent this lockup.  The lockup does not return upon subsequent reboots but DOES return upon returning from a shutdown.

The solution: Setting POST to always do a thorough test appears to prevent this problem.  Changing the option in the BIOS was forcing a thorough test.  If anyone else is having issues with broadcom drivers where they must boot to windows or are having a lockup at boot when their network card drivers load, in the BIOS change the POST mode to thorough.

Please report the success or failure of this method here =).

---

