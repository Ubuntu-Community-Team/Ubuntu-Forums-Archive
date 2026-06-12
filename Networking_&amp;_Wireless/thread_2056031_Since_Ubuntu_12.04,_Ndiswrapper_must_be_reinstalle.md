---
title: "Since Ubuntu 12.04, Ndiswrapper must be reinstalled after each update"
date: 2012-09-10
forum: Networking &amp; Wireless
---

### Post by Subdla on 2012-09-10
Since Ubuntu 12.04 upgrade, Ndiswrapper fails to load my wifi
driver.  Each time I update Ubuntu 12.04 (perhaps only major
updates?) I have to reinstall Ndiswrapper.  This always restores
my wifi.  So, the solution is to download the latest SourceForge
Ndiswraper (version 1.58rc1) and follow the instructions in the
Ndiswrapper Trouble Shooting Guide to install it.  You have to
remove the older versions of Ndiswrapper. Reinstalling Ndiswrapper
  	 	 	 	 	from the 12.04 cd does not work - it is version 1.57.  I have installed 
Ubuntu 32 bits on an Amd Athlon dual core machine - on a separate 
drive.  Can someone take note and fix 12.04 so that it does not wipe 
out Ndiswrapper evertime Ubuntu is updated?

---

### Post by chili555 on 2012-09-10
I think you have accomplished the opposite of what you want.>  Each time I update Ubuntu 12.04 (perhaps only major
updates?) I have to reinstall Ndiswrapper. This always restores
my wifi.I doubt you have to reinstall. I suspect the module *ndiswrapper* isn't loading. Adding a declaration to /etc/modules would probably have fixed it.

However:> the solution is to download the latest SourceForge
Ndiswraper (version 1.58rc1) and follow the instructions in the
Ndiswrapper Trouble Shooting Guide to install it.When you compile a source code file against your specific running kernel, you now for sure *MUST* recompile every time a newer kernel, also known as linux-image, is installed by Update Manager.

---

