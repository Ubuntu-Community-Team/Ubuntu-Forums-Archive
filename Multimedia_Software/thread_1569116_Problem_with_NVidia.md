---
title: "Problem with NVidia"
date: 2010-09-06
forum: Multimedia Software
---

### Post by dakochan on 2010-09-06
Hi,

I'm using Sony Vaio VPCCW26FG (CW Series). It's graphic card is NVidia GeForce GT 330M.
Recently I installed new driver from NVidia 256.53, but looks like this driver is not so stable on my notebook.
Sometimes the NVidia driver is successfully loaded, but sometimes its failed to load.

This is the last few lines of log message from Xorg.0.log:
```
(**) Sep 06 22:25:38 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 06 22:25:38 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 06 22:25:38 NVIDIA(0):     enabled.
(EE) Sep 06 22:25:39 NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0. 
(EE) Sep 06 22:25:39 NVIDIA(0):     Please check your system's kernel log for additional error
(EE) Sep 06 22:25:39 NVIDIA(0):     messages and refer to Chapter 8: Common Problems in the
(EE) Sep 06 22:25:39 NVIDIA(0):     README for additional information.
(EE) Sep 06 22:25:39 NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

Please help... :(

Regards,
DakoChan

---

