---
title: "KDE problems"
date: 2015-07-03
forum: Multimedia Software
---

### Post by devoar on 2015-07-03
Hello guys,

I am using kubuntu for a long time and I always had the same problem with the laptop I have for the past few years. I think it's related to the ATI/Intel hybrid crap on it because installing drivers tend to make it better.

Here is the problem. 

I installed fresh kubuntu 15.04 (but it is the same with older versions) on the machine. When KDE starts I have the following problems. Right click menu on browsers (chromium and firefox) disappear the moment it shows up. Sometimes it stays for few seconds but then again it disappears by itself for no reason. The system try popup menus also have the same behavior. And the K menu does the same thing. With installed ati driver from ati website it works a bit better. Now it takes like 3-4 seconds for the menus to disappear, but still they are gone by themselves even if I don't touch the machine. Now I have the following installed:

Build distro specific driver using this:  amd-driver-installer-14.501.1003-x86.x86_64.run
and also have these:
[FONT=monospace][COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-cirrus       - X.Org X server -- Cirrus display driver    [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-fbdev        - X.Org X server -- fbdev display driver     [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-intel        - X.Org X server -- Intel i8xx, i9xx display[/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-mach64       - X.Org X server -- ATI Mach64 display drive[/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-mga          - X.Org X server -- MGA display driver       [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-neomagic     - X.Org X server -- Neomagic display driver  [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-nouveau      - X.Org X server -- Nouveau display driver   [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-openchrome   - X.Org X server -- VIA display driver       [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-qxl          - X.Org X server -- QXL display driver       [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-r128         - X.Org X server -- ATI r128 display driver  [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-radeon       - X.Org X server -- AMD/ATI Radeon display d[/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-savage       - X.Org X server -- Savage display driver    [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-siliconmotio - X.Org X server -- SiliconMotion display dr[/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-sisusb       - X.Org X server -- SiS USB display driver   [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-tdfx         - X.Org X server -- tdfx display driver      [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-trident      - X.Org X server -- Trident display driver   [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-vesa         - X.Org X server -- VESA display driver      [/COLOR]
[COLOR=#FF5454]**i**[/COLOR][COLOR=#000000]   xserver-xorg-video-vmware       - X.Org X server -- VMware display driver   [/COLOR]

My Xorg log is full of these:

[/FONT][FONT=monospace][COLOR=#000000][   505.144] (II) fglrx(0): EDID vendor "LGD", prod id 748[/COLOR]
[   505.144] (II) fglrx(0): Printing DDC gathered Modelines:
[   505.144] (II) fglrx(0): Modeline "1366x768"x0.0   69.80  1366 1398 1430 1480  768 771 776 786 +hsync -vsync (47.2 kHz eP)
[   505.144] (II) fglrx(0): Modeline "1366x768"x0.0   48.25  1366 1398 1430 1534  768 771 776 786 +hsync -vsync (31.5 kHz e)
[   507.047] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   510.978] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   511.144] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   517.247] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   523.764] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   525.151] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   525.154] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   525.162] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   528.260] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   528.307] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   539.467] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   539.741] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   540.193] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   540.370] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   541.828] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   541.831] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   579.022] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   579.094] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   579.118] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   582.564] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   582.570] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   582.573] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   583.148] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000
[   583.160] (II) fglrx(0): Intel display surface mc addr for AMD: a84e0000

Now it takes about 8-10 seconds for the right click menu on any webpage to disappear. K menu so far looks stable as well as other OS menus, but for example if I use switchable graphics and switch to intel - everything starts disappearing in like 1-2 seconds. [/FONT]

---

### Post by Bucky Ball on 2015-07-03
*Thread moved to **Multimedia**.*

---

