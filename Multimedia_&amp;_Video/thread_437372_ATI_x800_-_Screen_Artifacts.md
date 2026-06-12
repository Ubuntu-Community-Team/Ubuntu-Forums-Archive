---
title: "ATI x800 - Screen Artifacts"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by Gorlist on 2007-05-08
Hi, today decided to install the fglrx ATI drivers using the following guide - [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

The installation of the drivers where easy to do, no problems - but using fglrx im getting lots of on screen Artifacts when on the desktop  (e.g. large garbled boxes of colour etc)..  -  no artifacts when ingame. 

The problem is if I use the standard ati drivers that come with Feisty I keep getting random black screens and system lock.

Running a Radon x800.. the hardware its-self seems fine (no issues in bimbos). 

Any suggestions?

Regards!

---

### Post by Gorlist on 2007-05-09
Hi, this morning reinstalled the drivers (after using the Synaptic Package Manager to remove Xorg) - im now finding i now can't engage 3d Acceleration, - when type in fglrxinfo to the terminal it comes up with:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

Any suggestions?

----
I had a chat with a gentlemen on IRC, and he suggest the Artifacts where caused by the current drivers, and to use Envy to get latest builds.

Though the drivers do seem to resolve the issue, I still have the above problem of lack of 3D Accel.
----

---

### Post by mwolfe on 2008-01-06
i have an x600 and after installing the ati drivers from the same site, i have screen artifacts in the lower right hand corner of the screen (black blotchy things) that will not go away. I've found that they do not show up until after one or two restarts after installing the drivers. The last 3 version have all done this to me. I install the newest driver, restart, and everything works good.. A day or so later i boot up and after being logged in for a minute or two i start getting all these screen artifacts, pretty much always in the bottom right hand corner, and when they first start to show up it seems they follow the cursor but that goes away and they end up in the bottom right.

Has anyone else seen a problem like this. I'm really considering starting all over with my ubuntu install.. I keep thinking a driver update will fix it but so far with 7.12 it still has this issue and i've uninstalled this driver and reinstalled several times with no luck.

---

### Post by Gus_T_Reer on 2008-01-07
I have an x850xt and use the fglrx restricted drivers that are provided with the distro. Both in Feisty (Beryl) and in Gutsy(compiz-fusion) I occasionally get lines of grey boxes where backgrounds are white, eg. against web pages in Firefox and in the white strips in the Appearance/Fonts box. I repeat that this is occasional and even restarting the machine has no effect. The only sure way for me to actually get rid of them is to completely power down the system and then power up again. Given this, the problem would appear to be some kind of initialisation problem. Can't say I've ever seen them associated with the cursor though.
So, sorry no solution but at least you're not alone.

---

### Post by mwolfe on 2008-01-08
While researching the problem a bit more, i found this thread:
[http://ubuntuforums.org/showthread.php?t=433737](http://ubuntuforums.org/showthread.php?t=433737)

which looks exactly like my problem except the original poster was using feisty (which i don't remember having this problem while i was using that). 
But there are screen shots and that is exactly my problem. 


For some reason when i first glanced at that post i thought it was multiple pages long.. Turns out its only one page and the solution is quite simple

just add 

```
Option		"XAANoOffscreenPixmaps"	"true"
```

in your device section..
Mine looks like

```
Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option      "XAANoOffscreenPixmaps" "true"
EndSection
```

---

