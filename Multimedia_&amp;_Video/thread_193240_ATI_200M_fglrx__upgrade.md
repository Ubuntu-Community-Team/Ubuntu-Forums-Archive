---
title: "ATI 200M fglrx : upgrade?"
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by EReckase on 2006-06-09
After my first attempt in getting the latest ATI drivers ( 8.25.18 ) working with my HP Pavilion dv8225nr, I got strange tearing issues when dragging windows around the desktop - it basically rendered the machine unusable.  (This was a fresh Dapper install.)  I reverted back to the 8.24.8 drivers that I was using in Breezy, and things are working pretty smoothly - but I've read a few posts indicating that the later drivers are really quite speedy, so I'd like to try them again.

I guess my first question is whether or not I should even bother, given the problems described at the [CCHTML Wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") regarding the dv5029us (a cousin of my laptop.)  

My second question is how I should attempt to upgrade the drivers - should I uninstall the 8.24.8 packages I installed manually prior to issuing the dpkg -i commands in the Wiki?  Given that the 8.24.8 drivers are working just fine without disabling the fglrx module in linux-restricted-modules-common, do I need to do this with the 8.25.18 drivers?

I'm quite the n00b with this stuff, but I can understand most instructions pretty clearly...any advice would be extremely valuable.

Many thanks...
E

---

### Post by EReckase on 2006-06-09
For reference (I don't know if these are good or bad) - these are the FPS I get with the 8.24.8 drivers:

glxgears -printfps
6469 frames in 5.0 seconds = 1293.687 FPS
6435 frames in 5.0 seconds = 1286.906 FPS
6435 frames in 5.0 seconds = 1286.872 FPS

fgl_glxgears -info
1157 frames in 5.0 seconds = 231.400 FPS
1344 frames in 5.0 seconds = 268.800 FPS
1336 frames in 5.0 seconds = 267.200 FPS

---

### Post by Ivhassel on 2006-06-09
You can check what chipset your card has with this:
```

lspci | grep ATI

```

If it says something like **R250**, or rather anything below R300, upgrading will break your 3D. The latest drivers don't work with cards, with a chipset = R2xx.

<edit>
Just looked at your laptop model, I can't find what graphics card you have, but it should turn up when you do 
```

lspic

```

If you're not sure that the newer drivers support your card, decide for yourself if a possible better driver is worth the risk of breaking it & having to fix it.

> 
glxgears -printfps
fgl_glxgears -info

That's a bit less than what i get, so I'd say at least your 3D is working, and you should have a fluent desktop...

---

### Post by EReckase on 2006-06-09
lspci returns:

```
lspci | grep ATI
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
0000:00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
```

---

### Post by Ivhassel on 2006-06-09
[QUOTE=EReckase]lspci returns:

```
lspci | grep ATI
0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
0000:00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
0000:00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)
```[/QUOTE]

I have absolutely no idea what card you have:-s

---

### Post by EReckase on 2006-06-09
VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

From everything I know about the machine, that's what the card is...

---

### Post by Ivhassel on 2006-06-10
[QUOTE=EReckase]VGA compatible controller: ATI Technologies Inc ATI Radeon XPRESS 200M 5955 (PCIE)

From everything I know about the machine, that's what the card is...[/QUOTE]

Yeah, sorry, I missed that.
But I still have no idea if you should update or not ...
Maybe look around on the ATI site.
If it's an older card, say a few years old, I wouldn't upgrade though, most older cards don't seem to like the most recent drivers.

---

### Post by EReckase on 2006-06-10
Oh - this is a brand spanking new laptop, no old hardware at all.  In fact, it's an AMD64 chip with 1 GB of RAM.  Regardless - how would you recommend upgrading the drivers if I *DID* want to?  The remaining parts of my question haven't been answered yet, so I'd love to hear how folks upgrade their systems.

---

### Post by Ivhassel on 2006-06-10
[QUOTE=EReckase]Oh - this is a brand spanking new laptop, no old hardware at all.  In fact, it's an AMD64 chip with 1 GB of RAM.  [/QUOTE]
Then I would certainly update.

[QUOTE=EReckase]
Regardless - how would you recommend upgrading the drivers if I *DID* want to?  The remaining parts of my question haven't been answered yet, so I'd love to hear how folks upgrade their systems.[/QUOTE]

by using apt-get, or a graphical frontend for it.

In a terminal:
```

sudo apt-get update
sudo apt-get upgrade

```

Or via Synaptic (gnome) or Adept (KDE). I'd recommend the latter if you have packages you can upgrade, other than your fglrx drivers.

Hope all goes well.

---

### Post by EReckase on 2006-06-11
After two more attempts, I'm going to assume that I have the same problems as the other HP laptop with the 200M graphics - the 8.25.18 drivers DO NOT WORK with this laptop (HP Pavilion dv8225nr).  I'll try the next version when it comes out.  If anyone has had success with this laptop, I'd love to hear about it.

:!:

---

### Post by Patsoe on 2006-06-11
Well, I've got a different laptop, but the same chipset. I have the new fglrx driver (8.25.18 that is) running here. It only works properly when I have a line saying "fglrx" in /etc/modules (I found this on the wiki page for the HP nx6125, my laptop). *edit: and after that, you need a real reboot, to get the modules loaded in the right order, because that's what this boils down to, I think.* If I leave that line out, I (reproducibly) lose glx functionality.

I'm using the ati driver whenever I don't need glx stuff though; I hate it how the fglrx driver keeps me from suspending to ram...

---

### Post by EReckase on 2006-06-11
OK, I haven't tried that yet.  I reverted back to 8.24.8, and that procedure was pretty straightforward, so I might try 8.25.18 again.  A few questions for you:

1.  What happened when you didn't have fglrx in your /etc/modules?  When I log in, I get all sorts of tearing issues and trying glxgears locks up my machine.

2.  What sorts of framerates do you get with the new drivers?  I'm curious if I should even bother.  I'm only trying this because I'm so shocked that my older 128 MB graphics card pretty much kicks this 200M card's *** in most 3d functions, and I'm not sure why.

Thanks!

---

### Post by Patsoe on 2006-06-12
1. The system would lock up when switching videomodes, eg. when going to a console. When I tried glx-stuff, it would say there was no GLX visual to adhere to. I sort of documented this problem in these threads: 
[just a whine about the GLX problem](http://ubuntuforums.org/showthread.php?t=189427)
[general talk about this  laptop model](http://ubuntuforums.org/showthread.php?t=189337)

2. I have about 700fps in glxgears I think. It's certainly not a fast graphics solution: it uses system RAM, and since this Turion only has a single memory channel, that means it's competing with a lot of other stuff for bandwidth...

---

### Post by HankB on 2006-06-12
Hi, Not sure if this will help you (or if you've already seen it.) I have the same video adapter in an HP laptop, also with a Turion processor and I'm running the AMD64 flavor of dapper. I followed the directions at [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) (choosing the alternative to "aticonfig --initial" ) and it seemed to work for me. glxgrears -printfps produced something over 1100 fps (and warmed the processor right up... And I wish I could recall what I looked at to determine processor speed! CRS takes it's toll ;) ) 

I returned to the 'ati' driver because the fglrx driver would not suspend or hibernate, but in the few days that I tried it, I did not notice other issues.

Not sure if it matters, but I upgraded from breezy and this was the first time I tried the fglrx driver.

The resulting xorg.conf is:

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
###     Load "synaptics"   # with a final 's'
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "Emulate3Buttons" "true"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

	Identifier  "Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
	Option	    "SHMConfig" "on"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x768" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x768" "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by onlybui on 2006-06-14
Well I upgraded the drivers in SUSE and it just made more problems... I always had to run mplayer from console.... SO did Dapper because everyone is using it and its got to be the easiest thing ever.... But as far as ATI 200M my frame rate is below 700 

0000:00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:11.0 IDE interface: ATI Technologies Inc ATI 437A Serial ATA Controller
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 04)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS480 [Radeon Xpress 200G Series]


and I get this error message 

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
456 frames in 6.2 seconds = 73.963 FPS
376 frames in 5.7 seconds = 65.811 FPS
418 frames in 6.8 seconds = 61.322 FPS

---

