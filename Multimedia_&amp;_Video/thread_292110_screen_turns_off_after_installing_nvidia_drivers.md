---
title: "screen turns off after installing nvidia drivers"
date: 2006-11-03
forum: Multimedia &amp; Video
---

### Post by dboot on 2006-11-03
Hello,

After installing the latest nvidia beta drivers my screen turns off. Only if I change my driver from "nvidia" to "nv" in /etc/X11/xorg.conf does gdm come up normally. I know gdm is starting because I can hear the login audio. I've been installing and uninstalling my nvidia driver at the command line for the past few days. I believe the driver is installed successfully but, again, when the gdm starts the screen turns off.

I've been loosely following [this ]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")tutorial to install nvidia drivers because it's the only tutorial I've found that talks about my video card: Geforce4 440 Go.

Any help would be appreciated!

---

### Post by roderikk on 2006-11-03
Hi,

I also have an nVidia, but it is a Geforce6 so I don't know if it works but I used this tutorial: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA) . Be aware that those are the beta drivers, so when you don't really know about it (not that I know much) don't use them. But the method described in the section to install the official drivers might still be usefull for you.

---

### Post by dannyboy79 on 2006-11-03
> **dboot said:**
> Hello,

After installing the latest nvidia beta drivers my screen turns off. Only if I change my driver from "nvidia" to "nv" in /etc/X11/xorg.conf does gdm come up normally. I know gdm is starting because I can hear the login audio. I've been installing and uninstalling my nvidia driver at the command line for the past few days. I believe the driver is installed successfully but, again, when the gdm starts the screen turns off.

I've been loosely following [this ]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")tutorial to install nvidia drivers because it's the only tutorial I've found that talks about my video card: Geforce4 440 Go.

Any help would be appreciated!
isn't this a legacy card? are you installing the lagecy drivers? I could be wrong but I am just trying to give you suggestions for a fix.

---

### Post by tseliot on 2006-11-03
try both point 7 and point 16 of the Problems Section:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by dboot on 2006-11-03
Thanks for the replies! Still having trouble.

roderikk, I've tried that install with no luck. Same problem occurs: when I run this "sudo /etc/init.d/gdm start" my screen turns off and i hear the login audio.

tseliot, I followed problems 7 before, including the variations, without any change. Point 10 also had no effect on my problem.

I just want to make sure this is clear: my gdm works fine when it doesn't use the nvidia driver. 

Do you think it would help if I uninstall my current driver (and go back to my original xorg.conf file), then follow this [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA) tutorial?

---

### Post by dboot on 2006-11-06
/var/tmp/bump

---

