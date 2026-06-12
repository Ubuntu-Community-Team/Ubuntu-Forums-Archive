---
title: "Breezy DRI"
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by jarrett.wold on 2005-10-15
I hate to be the one to send up the signal flare, but I'm at about wits end.  It appears that this release was rushed out the door with very little in regards to video testing.

I have tried two NVIDIA cards (Vanta, Geforce 4MX) and an ATI card (Radeon RV100) and the stock drivers for both on a stock install, DRI is broken.  I'm sure if I try more, I will get very nearly the same results.

In the NVIDIA case, DRI simply doesn't load; in the ATI case, DRI does load, but any GL apps run quit with an "Illegal Instruction".

I think this is absurd.  Even during Breezy Development, these were ongoing problems.  Breezy should not have been released with DRI broken on the default drivers, period.

Release Early, Release Often is a great philosophy for software so long as it is noted that it *is* in development.  Once, specifically open source, a build is declared release it is also assumed that it is stable.

Broken DRI is a critical enough issue, that this distro should not have shipped with these problems present.  I'm virtually certain that the plethora of posts regarding various problems with DRI are all in regards to some extremely small issue that was overlooked in the final XFree build.

At this point I'm seriously considering a jump to another distribution.  If something this obvious is overlooked in something declared release, it's time to find a fix, fast or start losing people from your user base.

---

### Post by snoochems on 2005-10-16
I was willing to give linux a go.  I started with ubuntu, and i can tell you that the lack of video has turned me off linux totally.  

I thought it was just a joke.  I tried hoary, i tired pre-release breazy, and now, i'm back to check to see if the ATI video issues had been sorted out yet, and they seem to have ignored the issue totally.

Oh well, back to windows for me.

---

### Post by psiko on 2005-10-16
I think I have identified the problem. The dri device have no permisions to all users and glxgears doesn't work good. Before I change the permisions o dri i had an output like this:
>  $ glxgears
libGL error: open DRM failed (Operation not permitted)
libGL error: reverting to (slow) indirect rendering

so I write that:
> # chmod 666 /dev/dri/*

That solved the problem temporaly, but I don't know whether the permisions sould be that or the applications should use dri in group video.

---

### Post by sebseb on 2005-10-16
I'd like to second this. Some bugs are understandable, but is just too big a deal for a desktop oriented distribution. 

psiko, it is not a permissions problem. The only error I see is 'illegal instruction'. I don't even have a Radeon or NVIDI card with binary-only drivers, I'm using the pretty much *ancient* open-source Matrox (mga) driver for my old G400. 

I can't believe AMD users (is there anyone on intel with this problem?) are left in the cold like this.

I filed a bug-report, so if you're having this problem as well, please CC or comment or something: [http://bugzilla.ubuntu.com/show_bug.cgi?id=17379](http://bugzilla.ubuntu.com/show_bug.cgi?id=17379)

---

### Post by hone on 2005-10-16
yeah, I can't seem to get the binary drivers for nvidia to get me 3d with the breezy packages.

---

### Post by claydoh on 2005-10-16
[quote=hone]yeah, I can't seem to get the binary drivers for nvidia to get me 3d with the breezy packages.[/quote]

For Nvidia drivers, have you run the command
[FONT=monospace]
> sudo nvidia-glx-config enable
[/FONT]

---

### Post by baker1tex on 2005-10-18
I believe I'm having a similar issue w/Breezy final release.  I have an Athlon64 on a Via K8T800Pro motherboard and Matrox G550.  OpenGL worked fine for me on Hoary, but when I attempt to run glxgears on Breezy, I get the following:

-----

$ glxgears
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
Error: couldn't get an RGB, Double-buffered visual

------

Here's the last several lines of my dmesg output:

[4296034.094000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4296034.094000] agpgart: Device is in legacy mode, falling back to 2.x
[4296034.094000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[4296034.094000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode
[4296051.037000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4296051.037000] agpgart: Device is in legacy mode, falling back to 2.x
[4296051.037000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 0x mode
[4296051.037000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 0x mode

------

I too am frustrated.  I really like Ubuntu, but am considering trying SuSE 10.  Upon installing Breezy, I opened up the System-->Prefrerences-->Screensaver and my computer locked up.  This is something I'm not used to occuring with Ubuntu.  The lack of 3d accelleration with my Matrox card is addition to the problem I was having accessing the Ubuntu update repositories last night because of invalide GPG signature (search the forums on that, there's lots of entries).    I'll attach my xorg.conf at the end of this post, I don't think there's anything wrong with it (it was copied from my working Hoary intall), but it's posted nonetheless.

Phil

-----
/etc.X11/xorg.conf :

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"no"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Matrox Graphics, Inc. MGA G550 AGP"
	Driver		"mga"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	VendorName   "Samsung"
	ModelName    "SyncMaster 213t 1600x1200"
	DisplaySize  423	370	# 1600x1400 96dpi
	HorizSync    30.0 - 81.0
	VertRefresh  60.0 - 60.0
	Option	    "dpms"	

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Matrox Graphics, Inc. MGA G550 AGP"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by baker1tex on 2005-10-18
I forgot to mention in my above post that I am running the i386 version of Breezy (with the 686 kernel).

Phil

---

### Post by etitor on 2005-11-19
[QUOTE=baker1tex]I forgot to mention in my above post that I am running the i386 version of Breezy (with the 686 kernel).

Phil[/QUOTE]
I run Breezy AMD64-k8. I also have a Matrox G550.

glxgears is working for me.

dmesg says this:
[   79.004848] [drm] Initialized mga 3.1.0 20021029 on minor 0: Matrox Graphics, Inc. MGA G550 AGP
[   79.005535] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   79.005549] agpgart: Putting AGP V2 device at 0000:00:00.0 into 1x mode
[   79.005571] agpgart: Putting AGP V2 device at 0000:01:00.0 into 1x mode
[   79.008605] [drm:mga_do_init_dma] *ERROR* failed to find status page!

and glxinfo says:
direct rendering: No

Now I suppose all this means I have no DRI, but somehow glxgears works OK (soft emulation?).

---

