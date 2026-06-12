---
title: "Gutsy/DRI/ATI open-source crash"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by project121 on 2007-12-20
<Plea for help>

I am unable to use DRI with the open-source ATI Radeon driver. I am running Gutsy on a Dell Inspiron 5150 with an ATI Radeon Mobility 9000. This should have full 2D/3D capabilities, but I have not been able to get direct-rendering to work using the [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) page. 

Also, I can't boot directly into X (brown screen of death -- and I've fixed the HAL/dbus timing issues); I have to Ctrl+Alt+F1 fast to get to the terminal, then sudo /etc/init.d/gdm restart (which opens a second display, since "Display :0 is busy"). 

Glxgears is 200-300 -- and is actually faster using the vesa driver. 

I am able to run the vesa driver, and am able to run the ati driver as long as I have "Option 	"DRI"	"off"" in my xorg.conf. 

$ glxinfo |grep "direct rendering"
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

At one point, due to frustration I did the fgrlx thing, but I've cleaned it up (it doesn't support my card):

$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

When I LIBGL_DEBUG=verbose glxinfo (after hitting Ctrl+alt+F1 to avoid the lockup at the login screen), this seems to be the reason:
XF86DRIQueryDirectRenderingCapable returned false

I've captured some crash data from the kernel and debug logs using "echo 1 | sudo tee /sys/module/drm/parameters/debug" -- hopefully it will help. 


Please see the attached outputs, and let me know if it's possible to get this thing working. Any help would be greatly appreciated!!!

---

