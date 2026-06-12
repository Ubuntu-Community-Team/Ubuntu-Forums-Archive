---
title: "Google Earth and AIGLX"
date: 2007-01-14
forum: Multimedia &amp; Video
---

### Post by tiagobt on 2007-01-14
I have an ATI Radeon X550 video card and I'm using it with the open source **ati** driver. For 3D acceleration, I use AIGLX. I have Beryl installed and working fine, and 3D applications usually run smoothly. Just for reference, my xorg.conf file is the following right now:

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Radeon X550"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"XAANoOffscreenPixmaps"
	Option		"AGPMode"       "8"
	Option		"AccelMethod"   "EXA"
	Option		"ColorTiling"   "on"
EndSection

Section "Monitor"
	Identifier	"Proview LP 717"
	Option		"DPMS"
	HorizSync	30-80
	VertRefresh	60-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon X550"
	Monitor		"Proview LP 717"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX"         "true"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

Also, direct rendering seems to be working fine, except for one error message:

```
$ glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
```

However, when I run Google Earth, the graphics are really slow and choppy, and the program crashes frequently. I thought the program output might help:

```
$ googleearth
libGL warning: 3D driver claims to not support visual 0x4b
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 412
Software fallback:ctx->Line.SmoothFlag
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 475
TODO - double side stencil !
***************************************************************************
*********************************WARN_ONCE*********************************
File radeon_mm.c function radeon_mm_alloc line 216
Ran out of GART memory!
Please consider adjusting GARTSize option.
***************************************************************************
Error: Could not get dma buffer... exiting
```

This error about GART memory also happens sometimes with 3D games, like Planet Penguin Racer.

Is there something I can do to solve the problem? Is my xorg.conf file OK? Is this a limitation of my graphic card or a limitation of AIGLX?

Thanks!

---

### Post by scrooge_74 on 2007-01-15
What about using close source binaries for that card?

---

### Post by tiagobt on 2007-01-15
> **scrooge_74 said:**
> What about using close source binaries for that card?

I guess you mean using the commercial FGRLX driver. Actually, I've been trying to use Beryl with AIGLX, and the latter is not compatible with FGRLX. Besides, using the open source driver ATI (or RADEON) with AIGLX has been giving me good results in general.

For the GART memory error, I found out that adding the following line to the "Device" section of xorg.conf solves the problem:
```
Option     "GARTSize" "64"
```
I'm not sure what this option implies, but at least I don't see the error message anymore.

About Google Earth's low performance, I found some people who claim that the r300 module (part of the ATI driver) is lacking a feature needed to accelerate Google Earth. Therefore, it falls back on software rendering and becomes really slow. One way to make it faster would be using a program called DRIconf and enabling the option "Disable low-impact fallback" (under the "Performance" tab). I installed DRIconf using apt-get and I even found the "Performance" tab. However, I see nothing that looks like "Disable low-impact fallback"... Can anyone help me on this one?

Thanks again.

---

### Post by tiagobt on 2007-01-16
I realize now why DRIconf doesn't allow me to choose the option "Disable low-impact fallback". The version of the r300 driver I'm using (Ubuntu repository) doesn't support this option. I even tried to force it by adding the following line to ~/.drirc:

```
<option name="disable_lowimpact_fallback" value="true" />
```

But the option doesn't seem to be recognized. Therefore, I guess Google Earth will remain unusable for the moment... :(

---

### Post by nubutu on 2007-03-19
Hi, Tiagobt

I've been looking for this thread this morning as it yesterday night gave me the hint I needed to solve my problem and I wanted to let you know what to do--although maybe you have already realized.

Basically, you're missing the "disable software fallback" option because you're not using the latest versions of the driver and libraries for 3D support. I found in the following thread

[http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)

that somebody has kindly packaged everything you need to (1) upgrade from xorg 7.1 to 7.2 (improved composite extension support and performance), (2) upgrade to the latest mesa libraries version, and (3) upgrade to the latest ati driver version.

After upgrading (some people encountered problems, many didn't, like myself), you'll be able to disable the option you were looking for and, guess what, GoogleEarth works.

Regards

PS. Well, I hope this works for your graphics card, mine it's not actually the same...

---

### Post by fait curieux on 2007-03-22
Thx a lot for this hint!, worked for me also on Radeon9600

---

### Post by Icarosaurus on 2007-03-30
hello,
works for me disabling the Low impact fallback.
but I experience problems in overlay (e.g. screen flickers when I try to watch at superimposed objects as panoramio pictures...
Anyone solved the problem?

Switching from Beryl to metacity causes the machine to hang!
Stars are white small squares but it is not a big deal to me.

I also tried the development version of mesa (6.5.3) it woks well (as for stars) but the problem persists.

Feisty
ati 9600
Xorg 7.2
Beryl
mesa 6.5.2 (dri)

---

### Post by nubutu on 2007-04-13
Hi

Well, I had some problems too, but didn't pay much attention to them in the first place. I also get squares instead of stars, as well as the flickering when moving and resizing the GoogleEarth window. I believe all this is related to the R300 driver not being fully developed--worth taking a look at their wiki, it seems things are going fast and I wouldn't be surprised to see a new release sooner than later.

More important than the problems above is that I noticed a 2D performance decrease, like windows' trails lingering on the screen for too long, high cpu usage in regular 2D desktop tasks and so on. I would like to know if any of you had experienced the same, for I remember somebody with the same sort of problem having a fix...

And yes, I can only use GoogleEarth if my desktop manager is Metacity, otherwise it just hangs. This looks more like something we can tackle, but I don't know how--possibly some xorg.conf settings? The thing is that I play 3D games with Metacity without no problem whatsoever...

And the last thing, you said you tried the last development Mesa version, but I don't get if that way the stars thing got solved or not; could you please clarify this?

Thanks

Mobility Radeon 9600/9700
Xorg 7.2, Mesa, R300 and all the relevant packages provided by Trevinho

---

### Post by Icarosaurus on 2007-04-13
2D permormance is quite good for me... but sometimes when cpu is working hard on some task, the mouse pointer freezes for some time on the screen. This is very annoying, and, maybe, it means that some graphics is still managed by software.

I can regularly use Googleearth in Beryl... but switching to metacity hangs the machine for me...
I don't know how to solve this problem.

Yes I downloaded the development mesa from git (see in the mesa3d site) and the stars problem got solved. But It gave me serious problems when shutting down or terminate sessions...so I gave up.
Nowadays, I cannot compile the newest git version of Mesa. Maybe they are making big changes in the source (such as implementing OpenGL 2.0) and it's still incomplete.
So...let's patiently wait... someone is working for us. My dream is to have a full harware support of radeon 9600 with aiglx and composite....
:roll:

---

### Post by iXneonXi on 2007-04-13
Hmm, I'm hopping in on this thread as someone who might be able to help, or be helped.
I have a 9600XT 256 under the hood, and have been hoping to get Google Earth working alongside any desktop effects.  Unfortunately, as stated above, Google Earth likes the restricted driver while the effects only work with the open source "radeon" driver.  Google Earth (and games) don't seem to like the free driver - they just run more sluggishly. However, when enabling desktop effects, things go crazy. There is a big performance hit and my applications are more likely to crash.
I'm on the Feisty Fawn right now.
Any recent developments in this area?

---

### Post by Icarosaurus on 2007-05-19
Just an update: Mesa 6.5.3 works a bit better ( the stars problem goes away).
You have to install correctly the DRI libraries to compile it...

---

