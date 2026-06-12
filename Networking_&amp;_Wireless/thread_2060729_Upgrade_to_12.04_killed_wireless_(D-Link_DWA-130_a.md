---
title: "Upgrade to 12.04 killed wireless (D-Link DWA-130 adapter)"
date: 2012-09-20
forum: Networking &amp; Wireless
---

### Post by rl7467 on 2012-09-20
I recently upgraded an old Dell Desktop to Ubuntu 12.04 (I'm not sure what Ubuntu version I upgraded from, but it was several years old). Under the old version, my wireless was working fine, using a D-Link DWA-130 V. E1 USB adapter. After the upgrade to 12.04, I have no wireless at all. Ndiswrapper and ndisgtk are both installed (the upgrade kept them, I did not re-install them after upgrade). Likewise, the driver, net8192su.inf, is installed, and the system knows the hardware is present. However, I have no wireless network device showing up - nothing to enable or configure.
Some threads indicate that ndiswrapper is no longer necessary, since Ubuntu began supporting the DWA-130 at some point between my earlier version of Ubuntu and 12.04. However, I didn't know that before I upgraded, and the upgrade kept it. 
At this point, I don't care whether to do something to force the Windows driver to work or disable that route and use the support within Ubuntu. I just want some way to get my wireless working without several more days of frustration. I would welcome any solutions. 
I have seen some suggestions that Ubuntu is looking in the wrong place for the Windows driver, and I can fix it by moving it to the right place. I would need very specific command and syntax to know how to accomplish that. Alternatively, I have seen suggestions to uninstall ndiswrapper, ndisgtk, and the windows driver (net8192su.inf) and use the built-in support. What are commands and procedures to accomplish that solution?
Thanks in advance for the help.I apologize for being so lame with the usage of the command line.

---

