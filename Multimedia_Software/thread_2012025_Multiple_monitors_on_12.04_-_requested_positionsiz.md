---
title: "Multiple monitors on 12.04 - requested position/size is outside the limit"
date: 2012-06-28
forum: Multimedia Software
---

### Post by Spartiate on 2012-06-28
Hi

I was running Ubuntu 12.04 with unity desktop and muliple monitors was not working. Going to System settings / displays did not work. The settings would default to "mirror" and whenever I would try to change it I would get an error like the following:

> 
[COLOR=#000000][FONT=Ubuntu]The selected configuration for displays could not be applied[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu]requested position/size for CRTC 148 is outside the allowed limit: position=(1280, 0), size=(1280, 800), maximum=(1600, 1600)[/FONT][/COLOR]
**Solution**

I finished right now to configure my laptop HP ProBook 4510s for using another monitor SAMSUNG SyncMaster S20B300B it took from me one hour and this is how I did it:

[LIST]
[*]Go to Terminal
[*]Type: gksudo amdcccle
[*]Catalyst Control Center will be open
[*]Go to Display manager => Multiple display desktop
[*]Click on monitor 1. Select the preferred resolution
[*]Click on monitor 2. Select the preferred resolution
[*]Drag each monitor to the correct side.
[*]Go to Display options => Enable Xinerama. This is very important. If you don't select this, your second monitor will work but you will not be able to drag any windows to it. Enabling xinerama allows you to drag windows across the screen.
[*]Click OK and reboot
[/LIST]
Good luck
Bye

---

### Post by joren02 on 2013-04-05
Thanks for this, saved me a lot of trouble :).

---

