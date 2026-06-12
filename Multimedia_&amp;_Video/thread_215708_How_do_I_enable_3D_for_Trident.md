---
title: "How do I enable 3D for Trident?"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by mojoman on 2006-07-14
Hi!

I'm running Dapper on a Toshiba Satellite 1800-504 (1Ghz Celeron, 256 MB RAM) with a Trident CyberBlade Ai1 (16MB) and I can't enable 3D. ](*,) 

I've tried "dpkg-reconfigure xserver-xorg" and it identifies the card as trident (though as i1 instead of Ai1) but it doesn't help.

When I run "glxinfo | grep rendering" the output is "direct rendering: No".

Also, DivX and Xvid get out of sync, which may be connected to this (I use Mplayer and have the right codec).

I'd really appreciate if anyone could give me some help with this! :)

---

### Post by az on 2006-07-14
I don't think there is any DRI for Trident cards.

---

### Post by Teroedni on 2006-07-14
well it seems it is supported


from man trident
> DESCRIPTION
       trident  is  an  Xorg  driver  for  Trident video cards.  The driver is
       accelerated, and provides support for the following framebuffer depths:
       1,  4, 8, 15, 16, and 24. Multi-head configurations are supported.  The
       XvImage extension is supported on TGUI96xx and greater cards.

SUPPORTED HARDWARE
       The trident driver supports PCI,AGP and ISA video cards  based  on  the
       following Trident chips:

       Blade       Blade3D,  CyberBlade  series  i1, i7 (DSTN), i1, i1 (DSTN),
                   Ai1,    Ai1    (DSTN),     CyberBlade/e4,     CyberBladeXP,
                   CyberBladeAi1/XP, BladeXP

       Image       3DImage975,  3DImage985,  Cyber9520,  Cyber9525, Cyber9397,
                   Cyber9397DVD

       ProVidia    9682, 9685, Cyber9382, Cyber9385, Cyber9388

       TGUI        9440AGi, 9660, 9680

       ISA/VLBus   8900C, 8900D, 9000, 9200CXr,  Cyber9320,  9400CXi,  9440AGi
                   These  cards  have been ported but need further testing and
                   may not work.



Are you using driver trident?


what does ```
sudo gedit /var/log/Xorg.0.log
``` gives

Post the whole text file here:)

---

### Post by cib on 2006-07-14
> **mojoman said:**
> Hi!

I'm running Dapper on a Toshiba Satellite 1800-504 (1Ghz Celeron, 256 MB RAM) with a Trident CyberBlade Ai1 (16MB) and I can't enable 3D. ](*,) 

I've tried "dpkg-reconfigure xserver-xorg" and it identifies the card as trident (though as i1 instead of Ai1) but it doesn't help.


Have you looked through your xorg configuration file to see if DRI is set? I don't know if the Trident card will support it but I'm assuming it is worth a shot as the onboard SiS video in my ancient IBM Aptiva (AMD K6-2 era) supports it.

It is a while since I have used Ubuntu but in Slackware the config file is /etc/X11/xorg.conf

The part of the file you are interested in should read something like (sort of - mine is hand edited at 3 in the morning after too much caffeine but it may serve as a guideline) this:

```
Section "Module"

## I edited out random stuff that had np bearing on DRI and made the Module section too long ##

# This loads the GLX module
    Load       "dri"
    Load       "glx"

EndSection

# **********
# DRI mode
# **********

Section "DRI"

    Mode   0666

EndSection
```

So - look through your xorg.conf file, see that if it is loading dri and glx.  As for DRI mode 0666 ??? You know - I can NOT remember why I did that but it may be important so I'll go look it up again.

> Also, DivX and Xvid get out of sync, which may be connected to this (I use Mplayer and have the right codec).


As for the out of sync - that can happen when you have onboard audio and video as they are (so far as I understand) both being timed by the CPU rather than by independant hardware.

I have heard the XINE has capabilities for resetting the sync.  If that is correct, then I would suggest using XINE as a backend for Totem.  Although - lets hear what others have to suggest - they may know something you can do in mplayer to achieve the same result.

Hope this helps somewhat.

Chris

---

### Post by mojoman on 2006-07-14
Thanks for all the tips.:D 

Here's what I found so far:

It should be a trident driver as it is supported and the card is detected as a trident card. 

My Xorg.conf does load the dri and glx modules (I might have configured this when I ran dpkg-reconfigure xserver-xorg). Also, the DRI mode is set for 0666 (probably from the automatic configuration, I didn't enter it).

As for the Xorg.0.log, I'll attach a copy. I you can get anything out of it I would very much appreciate it but it's quite extensive (not to mention way over my head ;)  ).

For good measure I'll attach a copy of my xorg.conf as well, just in case anyone can make anything out of it.

Once again, Thanks a bunch, I really appreciate all the help! :D

---

### Post by cib on 2006-07-15
OK, I've been thinking more on the Trident 3D issue.

I noticed this discrepancy - in your xorg.conf file you have the following:

```
Section "Device"
	Identifier	"Trident Microsystems CyberBlade/Ai1"
	Driver		"trident"
	BusID		"PCI:1:0:0"
	VideoRam	16000
	Option		"UseFBDev"		"true"
```

AND YET! In your Xorg.0.log file we see this interesting little warning tag:

```
(WW) TRIDENT(0): Option "UseFBDev" is not used
```

Unfortunately I cannot tell if this means that it is failing to load the Frame Buffer or if it means that you shouldn't load it.

FBDev is an Xorg 2d video driver - does this clash with the "trident" driver?  I don't know and Google is NOT being kind to me.

As a test you could comment that line out - like so:

```

#	Option		"UseFBDev"		"true"

```

Then re-start your x server (or reboot the machine) and see if that worked at all.  If it did - GREAT. If not...well then restore the line to its former glory and... we think again.

Is it possible that xorg 7.0 breaks some older drivers?  Does anyone have info on that?

CB

---

### Post by mojoman on 2006-07-15
Ok, I tested uncommenting the line:
```

# Option		"UseFBDev"		"true"
```

but I still get the output

```
glxinfo | grep rendering 
direct rendering: No 
```

I tried both uncommenting the line and entering "false" as option (I remember reading something about XFree86, where 1-0, true-false and yes-no were the options used and figured it might be the same here) but it didn't make any visible difference.

By the way, I did try the XFree86 as it too should support Trident but it crashed my computer (though I was using 5.10 at the time).

Thanks a lot for the effort you're all making. Not only are you very helpful but I'm also learning a lot. :D

More ideas and tips are most welcome though I won't be able to try it out until sometime next week as I'm of to my father-in-laws cabin outside Falun, Sweden where I'll be spending almost a week by the lake, pilfering his beer supply :D

---

### Post by cib on 2006-07-15
Hmmm.  I'm starting to run low on ideas - it should be working.

Lets do a quick recap:

You are loading the right driver (trident) and the needed modules (dri, glx and the sub-module GLcore).

The problem isn't UseFBDev True...

I checked sample config files for XFree86 that are supplied on a Toshiba (unofficial) support page (the driver was originally based on their X implementation and I don't think Xorg has deviated from the standards) and it looks good - like yours.

The Toshiba Unofficial Support page is at:
[http://newsletter.toshiba-tro.de/main/](http://newsletter.toshiba-tro.de/main/)
for those who are interested.

Right now I can't think of anything, I am afflicted by heat induced stupidity.

Enoy the cottage and we'll see if anyone comes up with anything over the course of a week.

Chris

---

### Post by mojoman on 2006-07-24
Hi again,

Still no progress though I have to admit I haven't been that active as I'm running out of ideas.

I'm considering trying the XFree86 package [http://www.xfree86.org]("http://www.xfree86.org")([www.xfree.org](www.xfree.org)) which explicitly supports trident CyberBlade Ai1 [http://www.xfree86.org/4.2.0/trident.4.html]("http://www.xfree86.org/4.2.0/trident.4.html").

However, I was running Breezy earlier and had the same problems that I now have and tried XFree86 and it totally crashed my system (some incompatibility problem with the installation script and I'm not the man to install it manually :-k ). Although I might not have these problems when installing XFree86 on Dapper it makes me a bit wary. Also, Dappar is, as far as I understand, also supposed to support Trident CyberBlade Ai1 so what's one to think? :confused: 

I'm something of a newbie so can anyone tell me what's the difference between XFree86 and Xserver? Are there any obvious drawback inherent in installing XFree86 on Ubuntu?

Thanks for all the help you been giving and enjoy the weather while its hot  and the beer while they are cold! 8)

---

### Post by PhilippWollermann on 2006-07-24
Hi,

> > I asked xorg to load glx, dri, and some other stuffs. I also set the
> DRI mode as 0666.
> 
> However glxinfo tell me that direct rendering is not enabled.

There is no functional trident 3d driver yet.
from [http://lists.freedesktop.org/archives/xorg/2005-April/007647.html](http://lists.freedesktop.org/archives/xorg/2005-April/007647.html)

It seems that you won't get accelerated 3D with this card. They started an accelerated driver ([http://dri.freedesktop.org/wiki/Trident](http://dri.freedesktop.org/wiki/Trident)) but it seems they never finished.

Installing XFree on your Dapper won't do anything but cause serious problems!

Philipp

---

### Post by cib on 2006-07-24
Xserver is a component of the X11 window system.

Xorg and XFree86 are two different implementations of X11.  Xorg is forked from XFree86 so there are probably more similarities than differences at this time (it was a licence or attribution change that caused this - I forget the exact reasons).

Anyway Xfree86 and Xorg BOTH claim to support (although apparently only in 2d accelerated mode) the Trident video card.

I quote from the Trident man page from my version of Xorg (6.8 I believe):

> 
trident  is an Xorg driver for Trident video cards.  The driver is accel*erated, and provides support for the following framebuffer depths: 1,  4, 8,  15, 16, and 24. Multi-head configurations are supported.  The XvImage extension is supported on TGUI96xx and greater cards.


I'm afraid I blindly read "accelerated" and thought "3d".  It would appear not, according to Phillpp's post.

Still, keep your fingers crossed - there may (hopefully) be an improved driver in future.

---

### Post by bryonhowley on 2006-07-25
Given the age of the card I would hold any hope of 3d.

---

### Post by cib on 2006-07-29
> **mojoman said:**
> Hi!

I'm running Dapper on a Toshiba Satellite 1800-504 (1Ghz Celeron, 256 MB RAM) with a Trident CyberBlade Ai1 (16MB) and I can't enable 3D. ](*,) 

I'd really appreciate if anyone could give me some help with this! :)

I may have fresh information and hope.  Or maybe not.

I poked around the Trident website and found on THIS page:

[http://www.tridentmicro.com/videographics/showmodel.asp?pro=cyberaladdin%20ai1](http://www.tridentmicro.com/videographics/showmodel.asp?pro=cyberaladdin%20ai1)

that they claim to supply drivers for Linux!  WOOOOO!

BUT!  The driver download pages show 404 on me.  So, undaunted I poked around on google and found sites claiming (CLAIMING - I haven't tried downloading and unzipping this file yet) to host a Trident Driver for Linux.  Here is an example link:

[http://www.opendrivers.com/driver/2682/trident-blade-3d-driver-for-linux-free-download.html](http://www.opendrivers.com/driver/2682/trident-blade-3d-driver-for-linux-free-download.html)

You can Google around and check other boards, perhaps, looking for info on the file "BladeXF86_SVGA.gz"  This is probably (if indeed it is real) a binary blob, proprietary file but...well if you really want 3d and it gets you 3d then, what the heck?

My idealistic side likes the philosophy of Richard Stallman and Theo de Raadt, but my pragmatic side sometimes just wants to play Doom3.

I'm going to see if I can find any qualifying info on this file, but I thought I'd pass along what I had straight away.

---

### Post by oss_monkey on 2006-08-03
Being another Trident Cyberblade user, I'm very interested in the option above. However, being a newbie as well, I'm scared as hell to run BladeXF86_SVGA.

I was able to extract it, but all it contained was an executable. I read somewhere that (I Googled "BladeXF86_SVGA") you had to kill X before running it, and even then, it looked for the config. :(

Scaredy-pants am I.

---

### Post by helvete on 2006-08-19
i have the file too but do not know where to extract it too, could someone point us in the right direction please...

---

### Post by mojoman on 2006-08-19
I don't know if running it is a good idea since it seem to be the XFree86 implementation and not Xorg (which is default in Ubuntu). However, I'm not att all sure. Perhaps someone knows about this? Is it possible to install both Xorg and XFree86 on Ubuntu?

Anyway, I've tried installing XFree86 (the full monty) but it didn't complete the installation, seriously screwed up my system and forced me to re-install. Because of this, I haven't tried this file. 

According to Toshiba support in Sweden (who were actually very helpful though stressing that they did not offically support Linux) Dapper and several other distros have these drivers by default but I cannot for the life of me get this to work (and I know of at least half a dozen other people on this forum who are in the same situation).

So, does anyone have any ideas? And is it safe to install XFree86 on Ubuntu?

Any help would be much appreciated.
/Mojoman

---

### Post by nickmcg on 2006-09-15
Similar problems:

I haven't installed the XFree86 driver - from what I read, it's a monolithic driver, rather than modular.

I've got the current source code for the trident driver, and there's a load of (seemingly) 3d functions which are commented out (well, not commented, but wrapped in #if 0 ... #endif directives).

I did try reinstating these, but compilation was problematic (I didn't have all the right tools installed).

I'll go back & revisit the code & let you know if I find anything

Cheers

Nick

PS, just looked, and found a newer version
google xserver-xorg-video-trident

Nick

---

### Post by nickmcg on 2006-09-17
I took the bull by the horns & ran BladeFX86_SVGA
...
..
.
It failed. It seems that it didn't understand the entries in the xorg.conf file.

(still trying on the trident driver compilation)

Nick

---

### Post by nickmcg on 2006-09-30
I have to admit defeat - my ignorance got the better of me!

---

### Post by mojoman on 2006-09-30
> **nickmcg said:**
> I have to admit defeat - my ignorance got the better of me!

You and me both. ;) 

I'm going to install some other OS on my laptop instead and I'm thinking about giving Debian a go. I still want to try XFree86 (they claim trident works with their driver) and it seem that XFree86 conflicts with Ubuntu. If that works (I won't have time to try it out until in a week or so) I'll post my findings here since I know that a lot of people are having problems with their trident cards.

/Mojoman

---

### Post by nickmcg on 2006-10-02
I don't know about xfree86 conflicting with ubuntu -  I installed it yesterday, but still no dri - the config program is terrible.
I still couldn't install the Blade_svga - again it seems that the xf86config file has the same syntax problems as xorg.conf. ](*,) 

I'm looking at updating the kernel. Version 2.6.18 has an experimental version of the trident diver, so I'm going to give that a try.

I'm getting braver now that I've got /home on a separate partition :) 

I'll keep you posted.

Cheers

Nick

---

### Post by deaglan on 2006-11-06
I am using a toshiba satellite 1800s with trident cyberblade Ai1 video card. I had this laptop several years ago and was running Debian Woody on it (with XFree86). I do remember struggling with X, but I eventually got it working. After getting this laptop back, I decided to try Ubuntu for its ease of install. Xorg is very sluggish.. I am running windowmaker. WIth ONE xterm open cpu usage from X can be up to 90% and 20% at idle. Granted, X is provided now by Xorg and not XFree86... the latter was nowhere near the poor performance I get now.

I have seen many posts claiming sluggishness is attributed to mozilla or KDE or GNOME... as I state above, this is NOT the case with this laptop.

I know this is of pretty much NO help - sorry. But it seems that its an Xorg problem.

btw: the performance lows as stated above are 2D - I tried running glxgears.. its painful.

---

### Post by tical2756 on 2007-02-25
BUMP.  I'm having the same problem and it's killing me.

---

### Post by krugger on 2007-03-23
Just got a laptop with this problem. Have you tried adding trident to the /etc/modules.

The problem is:

(EE) AIGLX: Screen 0 is not DRI capable

which is wrong as it could do DRI with XFree86

---

### Post by nickmcg on 2007-03-25
I installed XFree86 and, although much faster, I couldn't get dri working.
More importantly, though, I lost the top part of the screen display - the menu was still there, but not displayed - that section of the display was black, so I'm back with xorg

Nick

---

### Post by mojoman on 2007-03-25
> **krugger said:**
> Just got a laptop with this problem. Have you tried adding trident to the /etc/modules.

The problem is:

(EE) AIGLX: Screen 0 is not DRI capable

which is wrong as it could do DRI with XFree86

How should it be added? Would it be sufficient to just add trident on a new line in that file?

/mojoman

---

### Post by tical2756 on 2007-04-17
> **mojoman said:**
> How should it be added? Would it be sufficient to just add trident on a new line in that file?

/mojoman

Adding trident doesn't seem to be working.  Am I doing it right?

---

### Post by acaso on 2007-05-24
Trident has no DRI support in the kernel. You won't be able to enable 3D for that card.
"trident" kernel module has nothing to do with your card, it's an audio driver.

---

### Post by mojoman on 2007-05-24
> **acaso said:**
> Trident has no DRI support in the kernel. You won't be able to enable 3D for that card.
"trident" kernel module has nothing to do with your card, it's an audio driver.

I've given up hope on 3D but is DRI really the same thing? Isn't DRI necessary to watch for example video without going through the X-server?

---

### Post by pyrodrake on 2007-10-23
I'm sorry for resurrecting a dead post, but was just wondering if anyone got this officially working in some way/shape/form...  I've got a Toshiba Satellite 1805-S254 (archaic machine, really) running Gutsy Xubuntu (quite nicely, given the age of the machine itself).  As far as everything is concerned, I only have small issues with certain AVI compressions loosing sync after about 4-5 minutes of play time.  My main thing is I want to try to get StepMania to run on it, but am running into the problem:

```
00:01.897: OGL Max texture size: 2048
00:01.897: GLU Version: 1.3
00:01.897: Display: :0.0 (screen 0)
00:01.898: Direct rendering: no
00:01.899: X server vendor: The X.Org Foundation [1.3.0.0]
00:01.899: Server GLX vendor: SGI [1.2]
00:01.899: Client GLX vendor: SGI [1.4]
00:02.403: 
00:02.403: //////////////////////////////////////////////////////
00:02.403: Exception: There was an error while initializing your video card.
00:02.403: 
00:02.403:    PLEASE DO NOT FILE THIS ERROR AS A BUG!
00:02.403: 
00:02.403: Video Driver: OpenGL
00:02.403: 
00:02.403: Initializing OpenGL...
00:02.403: Your system is reporting that direct rendering is not available.  Please obtain an updated driver from your video card manufacturer.
00:02.403: 
00:02.403: //////////////////////////////////////////////////////
```

I've followed everything on here and still failed.  The video card is supposed to be Trident CyberAladdin-T.  Below are my xorg.conf and Xorg.0.log files.  Just wondering if there was any update on this, or if anyone found a solution.  Thanks, and sorry again!  ;)

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Trident Microsystems CyberBlade XPAi1"
	Boardname	"trident"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Screen	0
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Trident Microsystems CyberBlade XPAi1"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
	Load		"dri"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"trident"
	Busid		"PCI:1:0:0"
	Driver		"trident"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

Section "DRI"
    Mode   0666
EndSection

```

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux jaynet-pyromobile 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 23 06:02:15 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Trident Microsystems CyberBlade XPAi1"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "Synaptics Touchpad"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10b9,1644 card 0000,0000 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10b9,5247 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 10b9,5237 card 1179,0004 rev 03 class 0c,03,10 hdr 00
(II) PCI: 00:04:0: chip 10b9,5229 card 1179,0004 rev c3 class 01,01,f0 hdr 00
(II) PCI: 00:06:0: chip 10b9,5451 card 1179,0001 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:07:0: chip 10b9,1533 card 1179,0004 rev 00 class 06,01,00 hdr 00
(II) PCI: 00:08:0: chip 10b9,7101 card 1179,0001 rev 00 class 06,80,00 hdr 00
(II) PCI: 00:0a:0: chip 8086,1229 card 1179,0001 rev 0d class 02,00,00 hdr 00
(II) PCI: 00:11:0: chip 1179,0617 card 1000,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 00:11:1: chip 1179,0617 card 1800,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 01:00:0: chip 1023,8820 card 1179,0001 rev 82 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 168c,001a card 17f9,0008 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf7f00000 - 0xfdffffff (0x6100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x300fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:17:0), (0,2,5), BCTRL: 0x0500 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x24000000 - 0x27ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x23ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (0:17:1), (0,6,9), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[1] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x2c000000 - 0x2fffffff (0x4000000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x28000000 - 0x2bffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) Trident Microsystems CyberBlade XPAi1 rev 130, Mem @ 0xfc000000/25, 0xfbc00000/22, 0xf8000000/25, 0xf7ff8000/15
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf3ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x24000000 - 0x2400ffff (0x10000) MX[B]
	[1] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[2] -1	0	0xf7efd000 - 0xf7efdfff (0x1000) MX[B]
	[3] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[4] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[7] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[10] -1	0	0x0000eb40 - 0x0000eb7f (0x40) IX[B]
	[11] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[12] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x24000000 - 0x2400ffff (0x10000) MX[B]
	[1] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[2] -1	0	0xf7efd000 - 0xf7efdfff (0x1000) MX[B]
	[3] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[4] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[5] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[6] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[7] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[8] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[9] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[10] -1	0	0x0000eb40 - 0x0000eb7f (0x40) IX[B]
	[11] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[12] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x24000000 - 0x2400ffff (0x10000) MX[B]
	[5] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[6] -1	0	0xf7efd000 - 0xf7efdfff (0x1000) MX[B]
	[7] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[8] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[11] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000eb40 - 0x0000eb7f (0x40) IX[B]
	[17] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[18] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.3
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) v4l driver for Video4Linux
(II) TRIDENT: driver for Trident chipsets: tvga9000, tvga9000i, tvga8900c,
	tvga8900d, tvga9200cxr, tgui9400cxi, cyber9320, cyber9388, cyber9397,
	cyber9397dvd, cyber9520, cyber9525dvd, cyberblade/e4, tgui9420dgi,
	tgui9440agi, tgui9660, tgui9680, providia9682, providia9685,
	cyber9382, cyber9385, 3dimage975, 3dimage985, blade3d, cyberbladei7,
	cyberbladei7d, cyberbladei1, cyberbladei1d, cyberbladeAi1,
	cyberbladeAi1d, bladeXP, cyberbladeXPAi1, cyberbladeXP4, XP5
(II) Primary Device is: PCI 01:00:0
(--) Chipset cyberbladeXPAi1 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x24000000 - 0x2400ffff (0x10000) MX[B]
	[5] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[6] -1	0	0xf7efd000 - 0xf7efdfff (0x1000) MX[B]
	[7] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[8] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[11] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000eb40 - 0x0000eb7f (0x40) IX[B]
	[17] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[18] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x24000000 - 0x2400ffff (0x10000) MX[B]
	[5] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[6] -1	0	0xf7efd000 - 0xf7efdfff (0x1000) MX[B]
	[7] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[8] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[9] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[10] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[11] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[12] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[13] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000eb40 - 0x0000eb7f (0x40) IX[B]
	[20] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[21] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[22] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[23] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) TRIDENT(0): Depth 24, (--) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) TRIDENT(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) TRIDENT(0): RGB weight 888
(==) TRIDENT(0): Default visual is TrueColor
(**) TRIDENT(0): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(0): Using XAA for acceleration
(==) TRIDENT(0): Linear framebuffer at 0xFC000000
(--) TRIDENT(0): IO registers at 0xFBC00000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) TRIDENT(0): initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): VESA BIOS detected
(II) TRIDENT(0): VESA VBE Version 2.0
(II) TRIDENT(0): VESA VBE Total Mem: 16384 kB
(II) TRIDENT(0): VESA VBE OEM: Trident CYBER 8820
(II) TRIDENT(0): VESA VBE OEM Software Rev: 2.0
(II) TRIDENT(0): VESA VBE OEM Vendor: TRIDENT MICROSYSTEMS INC.
(II) TRIDENT(0): VESA VBE OEM Product: CYBER 8820
(II) TRIDENT(0): VESA VBE OEM Product Rev: KTT 7.1 (12.17)  
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
f000:370e: 01 ILLEGAL EXTENDED X86 OPCODE!
(II) TRIDENT(0): VESA VBE DDC not supported
(--) TRIDENT(0): Revision is 130
(--) TRIDENT(0): Found CyberBladeXPAi1 chip
(--) TRIDENT(0): RAM type is SGRAM
(--) TRIDENT(0): Using HW cursor
(--) TRIDENT(0): VideoRAM: 16384 kByte
(--) TRIDENT(0): TFT Panel 1024x768 found
(--) TRIDENT(0): Memory Clock is 60.00 MHz
(==) TRIDENT(0): Min pixel clock is 12 MHz
(--) TRIDENT(0): Max pixel clock is 115 MHz
(II) TRIDENT(0): Generic Monitor: Using hsync range of 31.50-48.00 kHz
(II) TRIDENT(0): Generic Monitor: Using vrefresh range of 56.00-65.00 Hz
(II) TRIDENT(0): Clock range:  12.00 to 115.00 MHz
(II) TRIDENT(0): Not using default mode "640x350" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "720x400" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "640x480" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "800x600" (hsync out of range)
(II) TRIDENT(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1024x768" (vrefresh out of range)
(II) TRIDENT(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1024x768" (hsync out of range)
(II) TRIDENT(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1152x864" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1280x960" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1280x960" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "832x624" (hsync out of range)
(II) TRIDENT(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1280x768" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1280x800" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1152x768" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1152x864" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1440x900" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) TRIDENT(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) TRIDENT(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(**) TRIDENT(0): Virtual size is 1024x768 (pitch 1024)
(**) TRIDENT(0): *Mode "1024x768@60": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) TRIDENT(0): Modeline "1024x768@60"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) TRIDENT(0): *Mode "800x600@60": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TRIDENT(0): Modeline "800x600@60"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) TRIDENT(0): *Mode "800x600@56": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TRIDENT(0): Modeline "800x600@56"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) TRIDENT(0): *Mode "640x480@60": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) TRIDENT(0): Modeline "640x480@60"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) TRIDENT(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) TRIDENT(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) TRIDENT(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) TRIDENT(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) TRIDENT(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) TRIDENT(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) TRIDENT(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) TRIDENT(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 -hsync -vsync
(==) TRIDENT(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B]
	[1] 0	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B]
	[2] 0	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B]
	[3] 0	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B]
	[4] -1	0	0x00100000 - 0x23ffffff (0x23f00000) MX[B]E(B)
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0x24000000 - 0x2400ffff (0x10000) MX[B]
	[9] -1	0	0xf7ec0000 - 0xf7edffff (0x20000) MX[B]
	[10] -1	0	0xf7efd000 - 0xf7efdfff (0x1000) MX[B]
	[11] -1	0	0xf7efe000 - 0xf7efefff (0x1000) MX[B]
	[12] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[13] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[14] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[15] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[16] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[17] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000eb40 - 0x0000eb7f (0x40) IX[B]
	[24] -1	0	0x0000ed00 - 0x0000edff (0x100) IX[B]
	[25] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) TRIDENT(0): Write-combining range (0xfc000000,0x1000000)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) TRIDENT(0): Initializing int10
(II) TRIDENT(0): Primary V_BIOS segment is: 0xc000
(II) TRIDENT(0): Overriding Horizontal timings.
(II) TRIDENT(0): Shadow off
(II) TRIDENT(0): H-timing shadow registers: 0xa3           0x00 0x84 0x94
(II) TRIDENT(0): H-timing registers:        0xa3 0x7f 0x7f 0x00 0x84 0x94
(II) TRIDENT(0): V-timing shadow registers: 0x24 0xf5 0x03 0x09           0x24 (0x08)
(II) TRIDENT(0): V-timing registers:        0x24 0xf5 0x03 0x09 0xff 0x00 0x24
(II) TRIDENT(0): Setting BIOS Mode Regs: 31 63 for: 1024x768
(II) TRIDENT(0): Found Clock  65.00 n=219 m=23 k=1
(II) TRIDENT(0): Using 1279 scanlines of offscreen memory for area's 
(II) TRIDENT(0): Using 8392704 bytes of offscreen memory for linear (offset=0x7ff000)
(II) TRIDENT(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		10 256x256 slots
(==) TRIDENT(0): Backing store disabled
(==) TRIDENT(0): Silken mouse enabled
(II) TRIDENT(0): Trident Video Flags: VID_ZOOM_INV  VID_OFF_SHIFT_4 
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event4
(**) Option "Device" "/dev/input/event4"
(--) Synaptics Touchpad touchpad found

```

---

### Post by mojoman on 2007-10-24
Well, I still got that same old computer though I only use it to play around with (I got a laptop as well). Right now it's running on Debian Lenny but I fear the HDD is about to give in. Anyway, I reckon that the best way to optimize it would be to compile a kernel, as this would give you the trident driver. If you've read this thread you might have seen some claim that the trident driver is only for the sound. This is wrong. There is a trident graphics driver though it doesn't have 3D support. However, there is experimental frame buffer support for it so I suspect that a custom kernel might very well go a long way. I just haven't gotten around to it yet...

---

### Post by fezouro on 2008-05-06
So, no good news for the faithful users about DRI/3D with xorg for the old Toshiba Satellite laptops?

---

### Post by songspring on 2008-05-16
Bumpalooza!

Anything new about these trident drivers on Toshiba Satellites + others?

Hello?

---

### Post by plewright on 2008-05-17
Same problem here too.

Installing ubuntu 8.04 from scratch - network install.  On my toshiba satellite, with trident cyberblade card also.

Thanks pyrodrake for the xorg.conf that helped me at least get X working at all.  Another thing I had added was    Option  "NoDDC"  to the Device section.

But now, I was hoping to get direct rendering and opengl working, see problem at top of my output from glxinfo...
```

# glxinfo 
name of display: :0.0
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
...
```

So, as you can see, I haven't got that yet.  Anyone get direct rendering or opengl working with this device?

---

### Post by ado@linux on 2008-05-20
I own a Compaq Armada 110 with the same (or very similar) Trident chipset.

I've been trying to figure out the problem, and, as far, I've the following:

[[COLOR="RoyalBlue"]DRI[/COLOR]]("http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure") is based on [[COLOR="RoyalBlue"]DRM[/COLOR]]("http://en.wikipedia.org/wiki/Direct_Rendering_Manager") which consists of two kernel drivers, a generic drm.ko module, and an vendor specific (vendorname_drm.ko or so) module.

If you look in the kernel source code (or DRM source) for the trident (vendor-specific) kernel module, you won't find it. DRM support for trident cards was dropped at the 2.4 branch of the kernel (look at [[COLOR="#4169e1"]this post[/COLOR]]("http://www.murga-linux.com/puppy/viewtopic.php?t=10757&sid=7b5dd0f28d420d799b2e612420d3ceeb") in the Puppy Linux Forums for a bit more of insight in the problem).

There's also "vendorname_dri.so" drivers somewere in every Ubuntu (and other distros) installation, but again, the trident-specific file of those drivers doesn't exist. I suppose these files are a kind of aditional support or something for getting DRI working.

I've tried different distros to see if there's any difference, as far all the following share the same problem, because all use the same xorg-trident-video driver:
> Ubuntu 7.04/7.10
Kubuntu 8.04
Ubuntu 8.04
Mandriva One 2008 Spring
openSUSE 10.3
Puppy Linux 4 (Live CD)

For reasons unknown to me, the best performing, when running glxgears was openSUSE. But all these distros lacks DRI (and specific DRM) support for Trident chips.

I also [[COLOR="#4169e1"]filed a bug report[/COLOR]]("http://bugzilla.kernel.org/show_bug.cgi?id=10681") (as and enhancement, not actually a bug) at the kernel.org bugzilla system. Since this cards are old, and will be out of the scene in a few years, I have little (very little) hope that someone at the kernel team put hands to work to bring DRI and full DRM support for these chips for the 2.6 branch of the kernel.

I'm not a programmer, I'm barely a "not-powerfull-at-all" user. But the sources are all out there. DRI support worked in the past, and could be possible to have it working again, but that's completely beyond my knowledge.

We can be saved, though, but only by Obi-Wan Kenobi. Or by a good programmer who owns a notebook with one of these chips and gets annoyed by it's lack of performance ;)

Greetings, Anibal from Buenos Aires

ps: my english it's far from good, sometimes close to gibberish, so ask me whatever you didn't understand about what i've said, but don't expect better english in the answer =P

ps2: I also tried to download, compile and install the lastest DRM and Mesa, with no luck, neither success or any other good outcome.

---

### Post by AdamWill on 2008-05-21
Yep, that's a very good summary. Without the DRM being ported to kernel 2.6 there's nothing we distros can do.

---

### Post by ado@linux on 2008-05-25
A little update.

Today, cleaning up the mess in the houyse I found an old Knoppix 3.4 Live CD, which uses a kernel from the 2.4.

No luck, again (i.e., not Direct Rendering). But, since it was a Live CD, I'm not sure about the validity of these results.

Greets, Anibal

---

### Post by songspring on 2008-05-26
I've been researching this same Trident Cyberblade issue on a Toshiba Satellite 1805 (p3-1000 with a gig of ram) running Ubuntu Dapper for months now.  Considering myself a newbie, after failing a few times and having to reconfigure x, I'm hesitant to delve too deeply into applying anything else unless I know it works.  

The problems I have with video are skipping, jerky play (like youtube stuff), out of sync audio on some divx files.  Ghosts of windows that I drag, unsatisfactory scrolling on graphic heavy web pages (like myspace, for example).

This machine orginally had XP installed and the video card worked fine.

I tried upgrading to Ubuntu 8.04, but I had a miniature desktop in the middle of the screen, and couldn't figure out how to solve that problem, so reinstalled 6.06.  I thought perhaps the newer version of Ubuntu might fare better with the old card, but never got a chance to test it.

I do wish some ambitious programmer would write a working driver for this card.  It and it's siblings are in quite a few older machines that otherwise function exceptionally with Ubuntu.  I want to keep using Ubuntu, but have been so frustrated a few times, I've been tempted to put xp back on it.

---

