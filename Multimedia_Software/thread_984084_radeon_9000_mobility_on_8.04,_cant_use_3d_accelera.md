---
title: "radeon 9000 mobility on 8.04, cant use 3d acceleration"
date: 2008-11-16
forum: Multimedia Software
---

### Post by pistolsnipe on 2008-11-16
first off:

gobook III

lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)

glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)

glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect

(setting verbose didnt seem to add any output)

ive tried switching to radeon and ati from vesa in xorg, always results in crash on boot

tried everything on this thread:
[http://ubuntuforums.org/showthread.php?t=727371](http://ubuntuforums.org/showthread.php?t=727371)

searched everywhere for a solution but switching drivers always results in xorg crashing on boot, my xorg default is about as generic as you can get and i had to downgrade from 8.10 to 8.04 in order to use the gtk config tool just to get 1024x768, i couldnt get manual configs to work right, 

like i said all changes result in either a blank screen or junk video on the screen when switching to radeon/ati in xorg
not that it matters but glxgears is ~600fps for me right now, 

any ideas?

---

