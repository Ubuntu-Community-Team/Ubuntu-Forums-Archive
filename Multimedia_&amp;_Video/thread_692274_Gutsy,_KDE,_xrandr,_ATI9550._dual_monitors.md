---
title: "Gutsy, KDE, xrandr, ATI9550. dual monitors"
date: 2008-02-09
forum: Multimedia &amp; Video
---

### Post by dsmithhfx on 2008-02-09
Hi,

I had dual monitors working well in xinerama with a Radeon 7000 on Feisty.

New computer, new gpu, Gutsy... apparently the new way is xrandr, but I haven't had much luck with a) finding a clear description of how to use it or b) hacking something together that works on my new setup (which is basically how I got the old setup to work).

Although in the command-line "xrandr -q" tells me I have two displays, and their respective specs, it is unresponsive to xrandr commands (e.g., "xrandr --output VGA --mode 1280x960 --rate 60"). 

I can use grandr to change resolution and refresh rates, although this cocks up the screen layout (leaving the menu bar marooned in the middle of the screen, for instance), 

Attempts at editing xorg.conf, using a couple of different guides
[http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html)
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

have not yielded any result other than x failing to start.

Here are the relevant bits from my latest attempt:
-------------------
Section "Device"
      Identifier      "ATI Technologies Inc RV350 AS [Radeon 9550]"
      Driver            "ati"
      BusID            "PCI:1:0:0"
#      Option            "UseFBDev"            "true"
      Option          "AccelMethod"   "EXA" #0902
      Option          "Monitor-VGA-0"  "FE700" #0902
      Option          "Monitor-DVI-0" "54e" #0902
EndSection

Section "Monitor" #0902
        Identifier      "FE700"
        Option        "Position" "0 0"
      Modeline "1280x960_60.00" 100.86  1280 1336 1464 1688   960  960  962  995 -HSync +Vsync
        Option "PreferredMode"  "1280x960_60.00"
EndSection 

Section "Monitor" #0902
        Identifier      "54e"
      Modeline "1024x768_60.00" 60.80  1024 1056 1128 1272   768  768  770  796 -HSync +Vsync
        Option "PreferredMode"  "1024x768_60.00"
        Option "RightOf"  "FE700"
EndSection

Section "Screen"
      Identifier      "Default Screen"
      Device            "ATI Technologies Inc RV350 AS [Radeon 9550]"
      Monitor            "Generic Monitor"
      DefaultDepth      24
          SubSection "Display" #0902 subsection
                  Depth 24
                  Virtual 2304 1024
          EndSubSection
EndSection
--------------------

I'm wondering if some of the code I copied from the debian guide is the wrong syntax?

Any help in getting this straightened out, even if just a pointer to other/better guides will be greatly appreciated...

Thanks!
-------------------------------------------------

OK, it was a syntax issue. You have to use "-0" with the device, e.g., "VGA-0", "DVI-0", and you have to first invoke/initialize xrandr for each display with the --auto command, e.g. "xrandr --output DVI-0 --auto", before it will respond. Now xrandr can be used to change resolutions and refresh rates for each display separately, on the fly -- "xrandr --output DVI-0 --mode 1024x768 --rate 85" "xrandr --output VGA-0 --mode 1024x768 --rate 60"

Adding 

    	SubSection "Display" #0902 subsection
      		Depth 24
      		Virtual 2304 1024
    	EndSubSection

To the "Screen" section of xorg.conf (and restarting x, and retyping the preceeding commands in terminal), enables display spanning by the command "xrandr --output VGA-0 --right-of DVI-0".

Cool! (still haven't quite got my head around relative positioning of displays in the virtual display area, how to control position of the menu bar etc.)

---

