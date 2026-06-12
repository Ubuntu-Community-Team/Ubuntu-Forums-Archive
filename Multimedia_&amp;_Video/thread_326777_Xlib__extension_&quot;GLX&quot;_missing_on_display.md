---
title: "Xlib:  extension &quot;GLX&quot; missing on display &quot;:0.0&quot;."
date: 2006-12-28
forum: Multimedia &amp; Video
---

### Post by TheFuzzy0ne on 2006-12-28
Hello everyone,

I know this question has been asked thousands of times before, but I spent all of yesterday afternoon and evening trying to find solutions, but to no avail. ](*,) 

Below, I have listed the multitude of things I have done in an attempt to try to fix my problem. SUggestions on what to do certainly weren't scarce, however, nothing I have tried has worked.

My AGP card is an NVidia GeForce 5200FX. I installed the proprietry drivers from NVidia's website a while back, and noticed an increase in the quality of my rendered graphics. XServer/KDE all seem to run with absolutely no problem.

I have changed /etc/X11/xorg.conf to make sure that all occurances of "nv" now say "nvidia" where applicable. In the "Module" section, I have commented out:

```
[FONT="Courier New"]Load "dri"
Load "GLCore"[/FONT]
```

and added:

```
[FONT="Courier New"]Load "GLX"[/FONT]
```

I have also tried uncomenting 'Load "dri"', again, as one post I read suggested doing this.

I have tried adding this section to /etc/X11/xorg.conf, following my reading another post:

```
[FONT="Courier New"]Section "Extensions"
  Option "Composite" "Disable"
EndSection[/FONT]
```

This did nothing, so I tried adding:

 ```
[FONT="Courier New"]option "RenderAccel" "true"
option "AllowGLXWithComposite" "true"[/FONT]
```

to the "Device" section, which again, does nothing...

I have attached a copy of my xorg.conf file, in case there is something obvious I have missed.

I have tried installing Open GL which did not work. There was a nice guide online at [http://www.ubuntuforums.org/showthread.php?t=157429]("http://www.ubuntuforums.org/showthread.php?t=157429")
Everything was going fine until I typed 'scons', and ended up with the following output, which I can't seem to find ANY information on fixing, (it's almost like it's not a fixable problem):

```
[FONT="Courier New"]scons: Reading SConscript files ...
:: Checking for libs
Checking for SDL_Init(SDL_INIT_VIDEO) in C library libSDL... yes
Checking for IMG_GetError() in C library libSDL_image... yes
Checking for glLoadIdentity() in C library libGL... yes
:: Compiling benchmarks for posix
:: Building binary message catalogs
Updating globs.pot

scons: warning: Two different environments were specified for target install,
        but they appear to have the same action: alias_builder(["install"], ["/usr/local/share/locale/it/LC_MESSAGES"])
File "po/SConstruct", line 51, in ?
scons: done reading SConscript files.
scons: Building targets ...
mo_builder(["po/es/LC_MESSAGES/globs.mo"], ["po/es/es.po"])
Updating po/es/es.po
........... done.
msgfmt: po/es/es.po: some header fields still have the initial default value
msgfmt: po/es/es.po: warning: PO file header fuzzy
                     warning: older versions of msgfmt will give an error on this
msgfmt: found 1 fatal error
scons: *** [po/es/LC_MESSAGES/globs.mo] Error 1
scons: building terminated because of errors.[/FONT]
```

Following other posts in other forums, I have ended up installing nvidia-glx, and nvidia-legacy (which has probably installed over my original driver).

**Here's the output for glxgears:**

```
[FONT="Courier New"]
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual[/FONT]
```

**And here's the output of glxinfo:**

```
[FONT="Courier New"]name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None[/FONT]
```

If anyone would be kind enough to offer any pointers on this, I am open to suggestions and would really appreciate the gesture.

All the best.

***_[COLOR="Purple"]Daz.[/COLOR]_***

---

### Post by Herodes on 2006-12-29
Having the exact same problem.

Has anyone made any progress on this ?

---

### Post by pickarooney on 2006-12-29
Did you install nvidia-glx ?

---

### Post by TheFuzzy0ne on 2006-12-29
Hi,

Yes, I had already installed nvidia-glx through aptitude. I think I did this before installing my NVidia proprietry drivers.

---

### Post by pickarooney on 2006-12-30
Make sure the proprietary drivers didn't delete nvidia-glx when you installed them.

---

### Post by tseliot on 2006-12-30
Try Envy, it should solve your problem:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by TheFuzzy0ne on 2006-12-30
> **tseliot said:**
> Try Envy, it should solve your problem:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Oh sweet! It worked a treat!!

A few notes.

envy_0.6.1-0ubuntu3_all.deb doesn't seem to exist on the server, so I downloaded envy_0.7.5-0ubuntu1_all.deb instead. 

It's important to note that: After typing "envy" and choosing the "install" option, envy might hang on Ubuntu's splash screen. To solve that problem press Ctrl+Alt+F1

Thank you so much tseliot!! :D

---

### Post by tseliot on 2006-12-30
> **TheFuzzy0ne said:**
> It's important to note that: After typing "envy" and choosing the "install" option, envy might hang on Ubuntu's splash screen. To solve that problem press Ctrl+Alt+F1
This is written under "Known Issues" in the same page

---

### Post by phizikal on 2007-09-24
I am having the same problem and i used envy also.

this is my xorg.conf.

> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

