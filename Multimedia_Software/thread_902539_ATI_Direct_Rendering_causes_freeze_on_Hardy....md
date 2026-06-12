---
title: "ATI Direct Rendering causes freeze on Hardy..."
date: 2008-08-27
forum: Multimedia Software
---

### Post by sungrazer on 2008-08-27
I have spent a few days scouring these (and other) forums but keep ending up at the same spot without fixing the problem.  So here's my trouble...

I have an AMD64 system with a Radeon 2600XT PCIe card, running Hardy. Initially I installed the ATI drivers fine but couldn't get direct rendering (DR) to work because of the Mesa problem.  I finally fixed that and now direct rendering works... but every time I run an OpenGL app of **any** kind, it runs for approx 3secs and the machine locks up.  The screen doesn't black out but the mouse and keyboard are frozen out.
Examples of apps that cause this are blender, glxgears, celestia, compiz, OpenGL screensavers... to name but a few.

If I disable DR via 'Option "DRI" "false"' in my xorg, then everything is fine except my machine runs like cr*p. I tried installing xserver-xgl (some folks seem to recommend it, others don't...) but that seriously messed up my display so I uninstalled.  I used Envy to install everything and that sort of worked but only once I used 'dpkg-reconfigure -phigh xserver-xorg' -- and that's where I am right now.

Here's my fgrlxinfo:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.1.7659 Release

```

Here's the pertinent parts of my glxinfo:
```

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
client glx vendor string: SGI
client glx version string: 1.4
GLX version: 1.2
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 2600 XT
OpenGL version string: 2.1.7659 Release

```

And my xorg which is partly a mish-mash of stuff I have taken from other posts and seems relatively stable...
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load "i2c"
        Load "bitmap"
        Load "ddc"
	Load "dri"
        Load "extmod"
        Load "freetype"
	Load "glx"
        Load "dbe"
        Load "int10"
        Load "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "on"
	Option "DRI" "true"    
	Option         "XAANoOffscreenPixmaps" "true"
	#BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


Section "DRI"
	 Mode 0666 
EndSection


```

Please help!!

---

### Post by markbuntu on 2008-08-27
You should have either VideoOverlay or OpenGLOverlay on, never both. What should work better though would be to have VideoOverlay and OpenGLOverlay "off" and TexturedVideo 'on". See this thread for more info about all that:


[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by sungrazer on 2008-08-27
Thanks for replying!

I turned VideoOverlay and OpenGLOverlay "off" and TexturedVideo "on".  Didn't fix it though -- OpenGL apps are still locking my computer up hard. ](*,)

Is there a debug stream or a log file that might show what it's doing right as it freezes? Does OpenGL create any sys logs like that?

---

### Post by eldirr on 2008-08-27
-Start the hardy with the live cd (for a clear xorg.conf file) 

-open the xorg.conf file and change the driver to "ati" 

-and add these ones to device section same with the driver; 
```
 	Option "BusType" "PCI"
	Option "AccelMethod" "EXA"
	Option "ExaNoComposite" "true"
	Option "MigrationHeuristic" "greedy"

```

-logout and login

-try to run glxgears and try to run compiz (if it doesn't work, try SKIP_CHECKS=yes compiz from terminal) It won't crash probably, but can be a little bit slower. 

-If this settings works, do the same with your install..

I hope that works. 

PS: there is a log file in /var/log/Xorg.0.log, that can be useful. You can check it for errors and warnings.

---

### Post by sungrazer on 2008-08-28
Thanks for wading in on this.

Making your recommended changes from the Live CD disabled direct rendering and, when used on a 'regular' boot, also put me back to the mesa drivers:

```
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

I do notice, however, that performance is now better than my previous non-DR state.  But I still only get ~900FPS on glxgears, which still sucks.

I tried using your edits but keeping the driver as fglrx.  This re-enabled DR and initially (5-10mins) after ctrl-alt-backspace-ing things were working well.  But then it died and, following a reboot, glxgears was freezing my machine again.  *sigh*

I can't see anything in the /var/log/Xorg* logs that look close to a warning or an error.

Ideas??

---

### Post by markbuntu on 2008-08-28
Do you have xserver-xgl installed by any chance?
If so you must remove it for fglrx to work properly. I ask because a symptom of having xserver-xgl is a reversion to mesa by fglrx.

```

sudo apt-get remove xserver-xgl

```

---

### Post by sungrazer on 2008-08-29
> **markbuntu said:**
> Do you have xserver-xgl installed by any chance?
If so you must remove it for fglrx to work properly. I ask because a symptom of having xserver-xgl is a reversion to mesa by fglrx.


No, it's not installed.  Running your code I did get the message:

```
The following packages were automatically installed and are no longer required:
  libglitz-glx1 libglitz1

```

So I removed them but I can't see as that would affect anything so didn't bother restarting X.  

Are there any diagnostics I can run to check for hardware/software clashes?  I just can't believe this isn't fixable -- my system is a very "ordinary" one (Dell Optiplex 740, ATI 2600XT card, 6GB RAM, Athlon X2 64).  No over-clocking, no fancy custom mods...  I really need the direct rendering for my work, so it's important I get it running.

Anyway, much appreciate all the help given so far.  Keep it coming! :)

---

### Post by sungrazer on 2008-08-29
Just a thought... is it possible that compiz is causing my machine to freeze?  I have it installed but I'm really not all that bothered about having the fancy desktop effects -- I'd rather just be able to run my PpenGL apps without issue.  If compiz could be the culprit, what the best way to cleanly uninstall it?

---

### Post by markbuntu on 2008-08-29
You don't need to remove it, just right click on you desktop and select Change Desktop Background/Visual Effects/None.

---

### Post by sungrazer on 2008-09-02
Bump. 

Anyone have any more insight regarding this Ubuntu problem I"m having?  Compiz isn't the culprit (I suspected as much) -- I have it disabled anyway.

---

### Post by sungrazer on 2008-09-11
Bump again...  Ideas??

---

### Post by markbuntu on 2008-09-12
You can try installing the latest ati driver. The one you have may be installed incorrectly which will cause it to revert to mesa, use Method 2 below:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

