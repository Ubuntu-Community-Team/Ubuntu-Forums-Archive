---
title: "Nvidia 319.17 driver problems"
date: 2013-05-07
forum: Multimedia Software
---

### Post by einstein**-7 on 2013-05-07
Using 12.04 64bit and trying to install the latest nvidia driver 319.17.etc with the install script from nvidia but it always says 'distribution install script failed'.
Tried with the existing nvidia-current 304.etc and with no luck and random error messages about missing directories and not able to create directories.
Sys has Jocky nvidia-common and nvidia-current installed.
Could use a little help!
thanks,

---

### Post by Bucky Ball on 2013-05-07
*Thread moved to **Multimedia & Video**.*

---

### Post by monkeybrain2012 on 2013-05-08
Don't install from Nvidia, it is tedious, error prone and you may run into dependency problems. You can install the Nvidia 319 driver on Precise by adding the xorg-edgers ppa

[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise)

If it works then you should disable the ppa after installing. Xorg-edgers is bleeding edge it pushes out constant updates and that can be risky.

Also install ppa-purge as advised in the website.

EDITED: and here is the hard way [http://thomas-romera.com/2013/04/16/Install-Optimus-Drivers-319-12-BETA-On-Linux/](http://thomas-romera.com/2013/04/16/Install-Optimus-Drivers-319-12-BETA-On-Linux/)

---

### Post by andrew.46 on 2013-05-08
> **monkeybrain2012 said:**
> 

EDITED: and here is the hard way [http://thomas-romera.com/2013/04/16/Install-Optimus-Drivers-319-12-BETA-On-Linux/](http://thomas-romera.com/2013/04/16/Install-Optimus-Drivers-319-12-BETA-On-Linux/)

It is a minor point but with the NVidia driver you would not normally have to blacklist nouveau by hand (as this guide suggests), the driver installation should do this for you.

---

### Post by einstein**-7 on 2013-05-08
> **monkeybrain2012 said:**
> Don't install from Nvidia, it is tedious, error prone and you may run into dependency problems. You can install the Nvidia 319 driver on Precise by adding the xorg-edgers ppa

[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise)

If it works then you should disable the ppa after installing. Xorg-edgers is bleeding edge it pushes out constant updates and that can be risky.

Also install ppa-purge as advised in the website.

EDITED: and here is the hard way [http://thomas-romera.com/2013/04/16/Install-Optimus-Drivers-319-12-BETA-On-Linux/](http://thomas-romera.com/2013/04/16/Install-Optimus-Drivers-319-12-BETA-On-Linux/)

OK, installed from ppa and all seemed good but on restart the greeter won't come up and starting xserver manually says that the nvidia kernel version 304  dosn't match driver version 319...
Any ideas, ?? the 319 driver package description says it includes the code to construct the new kernel but dosn't for some reason???????

---

### Post by monkeybrain2012 on 2013-05-08
Did you do all the upgrades when you install the driver? usually when you install something from xorg-edgers it pulls in a lot of updates (that's why you should disable the ppa afterwords) and you should allow all of them. The kernel should be updated also.

---

### Post by pogopuschel on 2013-05-09
> **andrew.46 said:**
> It is a minor point but with the NVidia driver you would not normally have to blacklist nouveau by hand (as this guide suggests), the driver installation should do this for you.
Yep. If nouveau is loaded, the 319.xx installer will blacklist the module. Maybe the author wants to prevent a reboot, but since that howto -for optimus- simply cannot work I have the idea that he is simply not knowing what he is doing/writing. Bad link :).

---

### Post by einstein**-7 on 2013-05-09
> **monkeybrain2012 said:**
> Did you do all the upgrades when you install the driver? usually when you install something from xorg-edgers it pulls in a lot of updates (that's why you should disable the ppa afterwords) and you should allow all of them. The kernel should be updated also.

Allowed the ppa to udate all and then tried to purge the old drivers and install from the command line-- no dm running-- this failed to, version mismatch.
Then tried from synaptic let it remove old and install new then rebooted right after and kernel version matched!
Found a thread that suggested that a reboot after driver installation was necessary for the nvidia kernel to be rebuilt and that sometimes it dosn't happen.  Maybe thats why my manual attempts didn't work since I simply changed drivers and then restarted X without rebooting.
Anyway, working now!
thanks

---

### Post by Bucky Ball on 2013-05-10
Good news. Please mark thread as solved to help others by editing first post, click 'Go Advanced' and change the [ubuntu] prefix to [SOLVED]. Thanks.

---

