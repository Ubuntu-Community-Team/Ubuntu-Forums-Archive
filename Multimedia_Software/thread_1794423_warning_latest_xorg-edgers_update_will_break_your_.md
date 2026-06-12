---
title: "warning: latest xorg-edgers update will break your system"
date: 2011-07-01
forum: Multimedia Software
---

### Post by beew on 2011-07-01
Hi,

Just have an update with the xorg-edgers ppa on my Xubuntu 11.04 installed on a 8 G usb drive (it is a test) and it killed Compiz.

"Compiz --replace" produces this error message
> compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
Running glxinfo produces this

> name of display: :0.0
Error: couldn't find RGB GLX visual or fbconfigTo make sure xorg-edgers is the culprit I used ppa-purge to remove it from my system and everything was back to normal. but just to be really sure I added the ppa and upgraded again. After rebooting Compiz was killed and glxinfo produced the same error.

I am therefore warning those who use this ppa not to update for a little while. Instead of purging the ppa again  I am staying where I am so I will know when the update to fix this is released.

---

### Post by beew on 2011-07-01
Got an update in xserver-common  and xserver-xorg-core and the problem appears to be solved. 

However I can't get Compiz to start automatically at startup, but there is no problem in  manually starting it with alt+f2 and then either "compiz --replace" or just "/usr/bin/compiz". I checked that the compiz entry is Session and Startup > Application Autostart has not changed (command set to /usr/bin/compiz)  

I would appreciate any help to get Compiz autostart again, maybe by clearing some config files. It doesn't seem to be a xorg problem as manually I can start compiz. I think I probably have messed up some of xubuntu's settings

---

