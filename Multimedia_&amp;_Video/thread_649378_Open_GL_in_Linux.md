---
title: "Open GL in Linux"
date: 2007-12-24
forum: Multimedia &amp; Video
---

### Post by gutsy_psu on 2007-12-24
Ok, as indicated by my post count, yes I'm a beginner, so hopefully this is an easy question.  I'm trying to install a windows only game via wine, and it's working fine up to the point of 3d graphics config.  The tutorial I am following says i must run in openGL (vs. direct3d).  But when I select open GL I recieve this message:
"Cannot obtain a list of available Display modes from the selected renderer and display adapter."\

When I try directX d3d i get "Cannot start selected renderer"

Any suggestions?  Thanks much.

---

### Post by gutsy_psu on 2007-12-24
update: from the documentation found at this page;
[https://help.ubuntu.com/community/Cedega](https://help.ubuntu.com/community/Cedega)

I ran the following in my session:

steven@steven-laptop:~$ glxinfo | grep 'direct rendering'
direct rendering: Yes
steven@steven-laptop:~$ glxgears
6705 frames in 5.0 seconds = 1340.983 FPS
6875 frames in 5.0 seconds = 1374.942 FPS


So OpenGL apparently is set up and working, but somehow the renderer isn't working correctly in reading it into the game. HELP!?!

---

### Post by Mike'sHardLinux on 2007-12-24
Hi.

What game are you trying to install? Often, each game has specific work arounds.

---

### Post by gutsy_psu on 2007-12-24
The game is Nascar Racing 2003 by Papyrus.  Not very well known outside the nascar crowd, so guessing that may not help much, but would still appreciate any feedback/suggestions, thanks!:)

---

### Post by weblordpepe on 2007-12-25
One trick you could try is using the **winecfg** program to create a virtual Windows desktop.
Occasionally when Windows apps are inside Wine, they can have issues with detecting the screen resolution. Serious Sam is like that. It goofs up when run normally, but when Wine apps are told to exist inside their virtual Windows desktop, Serious Sam runs good.

---

### Post by gutsy_psu on 2007-12-25
> **weblordpepe said:**
> One trick you could try is using the **winecfg** program to create a virtual Windows desktop.
Occasionally when Windows apps are inside Wine, they can have issues with detecting the screen resolution. Serious Sam is like that. It goofs up when run normally, but when Wine apps are told to exist inside their virtual Windows desktop, Serious Sam runs good.

Thanks, I'll have to check that out then...

---

### Post by gutsy_psu on 2007-12-25
ok that doesn't seem to fix it (wine cfg to create XP virtual desktop)

, the problem seems to be that it can't start the selected renderer, but I'm not sure what renderer it's trying to use, and or how to change it.  any suggestions?

---

### Post by gutsy_psu on 2007-12-25
I see these lines from the games configuration file, which may be causing the problems?
][Graphics]

boardIndex=0

fullScreen=1

lastDesktopBPP=24

lastRendererDLL=rend_dxg.dll


And the rend_dxg.dll is in the games directory

The tutorial also mentions a desktop = line in the wine config file, which I can't seem to find?

---

### Post by gutsy_psu on 2007-12-26
any ideas?

---

