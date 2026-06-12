---
title: "Nvidia X Server Settings Won't Stick!"
date: 2008-08-31
forum: Multimedia Software
---

### Post by mxcrowe on 2008-08-31
How do I make the settings in Nvidia X Server Settings stay the way I want them after reboot?  I configured everything the way I want it, then select "save to X config file".  When I check the xorg.conf file in /etc/x11, it seems to have the right settings (1280x1024_75 +0+0; nvidia-auto-select +0+0).  But when I reboot the system, it reverts back to a 60hz refresh rate.  I check the xorg.conf file again, and it still seems to be set for 75hz.  Why won't these settings stay the way I put them??

---

### Post by mxcrowe on 2008-09-01
Does anyone know how to stop the refresh rate reverting to 60hz every time I start Ubuntu?

---

### Post by cdtech on 2008-09-01
sudo nvidia-settings
used to configure the NVIDIA graphics driver.

---

### Post by mxcrowe on 2008-09-01
Yes, I did that!!!!!!  I don't have any problem using the interface, and it saves the xorg.conf file fine, as far as I can tell. Everything looks fine until I reboot.  Even the login screens are 1280x1024x75hz, but as soon as the desktop loads, it reverts to 60hz.  Something is broken here!

---

