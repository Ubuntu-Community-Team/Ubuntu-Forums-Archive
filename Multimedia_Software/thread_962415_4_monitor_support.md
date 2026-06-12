---
title: "4 monitor support"
date: 2008-10-29
forum: Multimedia Software
---

### Post by bupe on 2008-10-29
I just started experimenting with ubuntu 8.04 and on my laptop I'm loving it.

Yesterday I installed it on my desktop machine which has 2xati hd3870 videocards and I have 4 monitors attached to it (2x19" LCD, 1x24" LCD, 1x42" LCD TV). Their native resolutions and aspect ratios are not the same and in windows I was able to easily configure them using CCC but I simply cannot find a straightforward tool in Ubuntu that would allow me to set different resolutions for the different displays.

I searched the forums and found a post which showed a youtube video of merging 6 displays but in that case all of them were using the same resolution...

What I want to achieve:

1280x1024 on 19" no. 1
1280x1024 on 19" no. 2
1366x768 on LCD TV
1920x1200 on 24"

In windows the LCD TV was on the far left (actually this is in front of my sofa so doesn't really matter where it is compared to the others as long as I can set it up separately), next I attached the 24" and the two 19" were on the right of the virtual desktop. 

Any useful input on how to set this up properly would be much appreciated.

Best,
Peter

---

### Post by alfalfa31 on 2008-10-29
> **bupe said:**
> I just started experimenting with ubuntu 8.04 and on my laptop I'm loving it.

Yesterday I installed it on my desktop machine which has 2xati hd3870 videocards and I have 4 monitors attached to it (2x19" LCD, 1x24" LCD, 1x42" LCD TV). Their native resolutions and aspect ratios are not the same and in windows I was able to easily configure them using CCC but I simply cannot find a straightforward tool in Ubuntu that would allow me to set different resolutions for the different displays.

I searched the forums and found a post which showed a youtube video of merging 6 displays but in that case all of them were using the same resolution...

What I want to achieve:

1280x1024 on 19" no. 1
1280x1024 on 19" no. 2
1366x768 on LCD TV
1920x1200 on 24"

In windows the LCD TV was on the far left (actually this is in front of my sofa so doesn't really matter where it is compared to the others as long as I can set it up separately), next I attached the 24" and the two 19" were on the right of the virtual desktop. 

Any useful input on how to set this up properly would be much appreciated.

Best,
Peter

I think my setup may be a bit closer than most of the tutorials you have found.  I'm running what amounts to two separate displays across four monitors.  I have two 22" monitors and two 17" monitors.

What you're trying to do (and correct me if I'm wrong) is have the two 19's as one monitor and the 24 as another with the TV as a third, right?

If that isn't what you're doing, it might be what you should do.  If you want to run each as a separate monitor (and why on earth would you want that, at least with the 19's), you may run into a few hiccups with the resolutions and confusing the windowing system with task bar widths and such. 

What I recommend (and the positions are irrelevant) is that you run the 19's as a big 2560 X 1024 display and run the TV and the 24 as their own displays.   
```
______________________  ____________  ________________
|..........|..........|.|...........|.|...............|
|..........|..........|.|...........|.|...............|
|...19"....|...19"....|.|.....TV....|.|......24"......|
|......2560X1024......|.|.1366x768..|.|...1920x1200...|
|__________|__________|.|___________|.|_______________|
Fig 1.A
```

The questions I have are:

What ATI driver version are you running?
Is the layout pictured in Fig 1.A (I've been reading too many technical manuals) what you're looking for?
Do you feel comfortable editing the xorg.conf file you got from my other post?

Aaron

---

### Post by bupe on 2008-10-29
That is exactly what I'm looking for.

Answers to your questions:

- I will use whatever you tell me to use. I'm just about to reinstall ubuntu as my experimentation with envyNG and the manual installation of the 8.10 drivers from ati left me with quite a big mess...
- the layout looks exactly like the one I want except I have the 19" displays on the other side
- I have a broadcom based asus wireless router for which I'm running a custom firmware (openwrt) and I was experimenting on it with other flavors as well which required some config file editing so I'm confident that I'll be able to do that :)

Looking forward to your recommedations (I'm writing this from vista... :() before I dive into the linux world again.

Thanks,
Peter

---

### Post by alfalfa31 on 2008-10-30
For the sake of letting you know, I had a dumb terminal hooked up to the system while I distilled my xorg.conf file down to what it is now.  If you don't have one, the process will be more difficult, but we'll still get it working.

The first thing you need to do is install the OS.  'Nuff said...

After that, get the closed source ATI drivers and install them according to a tutorial.

[This should be a good one]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

Start with the below xorg.conf file and see if it starts.  If it doesn't, you'll need to be ready with the one that originally got one of the monitors working (the default install xorg.conf).  That way you can post the error logs and X startup logs.  What that means is, back up the freakin' conf files before overwriting them...

```

Section "ServerLayout"
	Identifier   "Default Layout"
	Screen    0  "screen1" 0 0
	Screen       "screen2" LeftOf "screen1"
	Screen	     "screen3" LeftOf "screen2"
	InputDevice  "Generic Keyboard"
	InputDevice  "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load	     "dbe"
	SubSection   "extmod"
		Option 	    "omit xfree86-dga"
	EndSubSection
	Load 	     "glx"
	Load         "dri"
	Load	     "freetype"
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
	Identifier   "monitor1"
EndSection

Section "Monitor"
	Identifier   "monitor2"
EndSection

Section "Monitor"
	Identifier   "TV"
EndSection

Section "Device"
	Identifier  "ati1"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "UseFastTLS" "0"
	Option	    "HWCursor" "on"
	Option	    "BackingStore" "false"
	Option 	    "XAANoOffscreenPixmaps" "true"
	Option	    "OpenGLOverlay" "off"       
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
	Option	    "TextureVideo" "true"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "DesktopSetup" "horizontal"
	BusID       "1:0:0"
EndSection

Section "Device"
	Identifier  "ati2"
	Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "BackingStore" "false"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "OpenGLOverlay" "off"        
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "TextureVideo" "true"
        Option      "OverlayOnCRTC2" "0" # this should tell the system not
                                         # to clone or stretch the desktops.
        Option      "DesktopSetup" "horizontal"
	BusID       "2:0:0"
EndSection

Section "Screen"
	Identifier "screen1"
	Device     "ati1"
	Monitor    "monitor1"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "screen2"
	Device     "ati2"
	Monitor    "monitor2"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "screen3"
	Device     "ati2"
	Monitor    "TV"
	DefaultDepth     24
EndSection

Section "ServerFlags"
	Option    "AllowMouseOpenFail" "on"
	Option    "IgnoreABI" "on"
	Option    "AIGLX" "on"
EndSection

Section "Extensions"
	Option    "Composite" "disable"
	Option	  "Damage" "true"
EndSection

Section "DRI"
	Group     0
	Mode      0666
EndSection

```

The above file should be used as a roadmap to success, because it likely won't be exactly as you need it.  You may need to change some "LeftOf's" or maybe even add a device (though I don't think you will).  I'm sure you'll want to personalize it by adding actual device names for your stuff (what's lamer than "TV" for a name?) and maybe throw in a comment or two for future reference.

Adjusting resolutions should be done in the OS (System -> Preferences -> Screen Resolution in Gnome), so you won't need a bunch of modelines in the conf.

Looking forward to hearing what breaks...

Aaron

---

### Post by bupe on 2008-11-01
I tried adjusting the code you gave and came up with this:

```
Section "ServerLayout"
	Identifier   "Default Layout"
	Screen    0  "screen1" 0 0
	Screen       "screen2" LeftOf "screen1"
	Screen	     "screen3" LeftOf "screen2"
	InputDevice  "Generic Keyboard"
	InputDevice  "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load	     "dbe"
	SubSection   "extmod"
		Option 	   "omit xfree86-dga"
	EndSubSection
	Load 	     "glx"
	Load         "dri"
	Load	     "freetype"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "hu"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "Monitor"
	Identifier   "VX9x2"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "L245WP"
EndSection

Section "Monitor"
	Identifier   "42C3001P"
EndSection

Section "Device"
	Identifier  "ati1"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "UseFastTLS" "0"
	Option	    "HWCursor" "on"
	Option	    "BackingStore" "false"
	Option 	    "XAANoOffscreenPixmaps" "true"
	Option	    "OpenGLOverlay" "off"       
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
	Option	    "TextureVideo" "true"
	Option	    "OverlayOnCRTC2" "1"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ati2"
	Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "BackingStore" "false"
        Option      "XAANoOffscreenPixmaps" "true"
        Option      "OpenGLOverlay" "off"        
        Option      "UseFastTLS" "0"
        Option      "HWCursor" "on"
        Option      "TextureVideo" "true"
        Option      "OverlayOnCRTC2" "0" # this should tell the system not
                                         # to clone or stretch the desktops.
        Option      "DesktopSetup" "horizontal"
	BusID       "PCI:2:0:0"
EndSection


Section "Screen"
	Identifier "screen1"
	Device     "ati1"
	Monitor    "VX9x2"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "screen2"
	Device     "ati2"
	Monitor    "L245WP"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "screen3"
	Device     "ati2"
	Monitor    "42C3001P"
	DefaultDepth     24
EndSection

Section "ServerFlags"
	Option    "AllowMouseOpenFail" "on"
	Option    "IgnoreABI" "on"
	Option    "AIGLX" "on"
EndSection

Section "Extensions"
	Option    "Composite" "disable"
	Option	  "Damage" "true"
EndSection

Section "DRI"
	Group     0
	Mode      0666
EndSection
```

The results:

I just realized that the two 19" displays were connected to different cards so I reconnected them and now the 19" displays are connected to the primary card while the 24" and the 42" displays are connected to the secondary.

As I said the first card has the two 19" displays connected, and they are detected as one big 2560x1024 screen, so those work.

However I'm not getting any signal from the secondary card with the 24" and 42" connected... any idea what could cause this? Where should I look for errors?

Thanks,
Peter

EDIT

I just read a short article about xorg.conf editing on [www.linux.com](www.linux.com) ([Editing basics for the xorg.conf file]("http://www.linux.com/feature/118108") and it helped me finding the X server log file (/var/log/Sorg.0.log).

According to that 

```
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.54.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.542                    
(II) ATI Proprietary Linux Driver Build Date: Oct  3 2008 17:42:12
(WW) fglrx: More than one matching Device section for instances
	(BusID: PCI:4:0:0) found: ati2
(--) Chipset Supported AMD Graphics Processor (0x9501) found
(--) Chipset Supported AMD Graphics Processor (0x9501) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
```

my secondary adapter is located at PCI:4:0:0 so I changed the Device section and restarted the X-server according to the articel by pressing Ctrl-Alt-Backspace but that didn't solve my problem of not getting a picture on the 3rd and 4th displays.

However going through the log file I found this:

```
(II) fglrx(1): === [atiddxPreInit] === begin
(II) fglrx(1): PCI bus 4 card 0 func 0
(II) fglrx(1): Creating default Display subsection in Screen section
	"screen2" for depth/fbbpp 24/32
(**) fglrx(1): Depth 24, (--) framebuffer bpp 32
(II) fglrx(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(1): Default visual is TrueColor
(**) fglrx(1): Option "OpenGLOverlay" "off"
(**) fglrx(1): Option "VideoOverlay" "on"
(**) fglrx(1): Option "DesktopSetup" "horizontal"
(**) fglrx(1): Option "OverlayOnCRTC2" "0"
(**) fglrx(1): Option "UseFastTLS" "0"
(EE) fglrx(1): Multiview is not supported on the first adapter; this screen will now shutdown.
(EE) fglrx(1): PreInit failed
(II) fglrx(1): === [atiddxPreInit] === end
(II) UnloadModule: "fglrx"
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
```

So it seems something is preventing the X server to initialize screen2. Adter this there is no mention of screen3 whatsoever...

---

### Post by bupe on 2008-11-01
It seems I'm not the only one dealing with this issue...

[two ati graphic cards HD 3650 with fglrx driver doesn't work together]("http://ubuntuforums.org/showthread.php?t=920898")

[quad head (4 monitor) ATI X1300 and X1900]("http://ubuntuforums.org/showthread.php?t=959713")

Regarding MultiView I found this ([Question regarding ATI MultiView]("http://forum.beyond3d.com/showthread.php?t=46660"):

> according to 8.1 release notes:
New Features
Catalyst 8.1 introduces MultiView™ support. This feature provides for hardware accelerated OpenGL rendering across multiple graphics adapters. MultiView™ will provide hardware accelerated 3D rendering in a system containing multiple graphics cards on an extended desktop arrangement. This feature will allow for the rendering performance and additional frame buffer resources to be evenly shared with the second and third graphics adapters. This allows for a 3D application to have the same performance running on a secondary or third display device as if it were running on the primary display device. This feature will be supported under Windows XP (32 and 64 bit versions), Windows Vista (32 and 64 bit versions), and the Linux operating system. Product support includes:

· ATI Radeon™ HD 3870 series
· ATI Radeon™ HD 3850 series
· ATI Radeon™ HD 2900 series
· ATI Radeon™ HD 2600 series
· ATI Radeon™ HD 2400 series
· ATI Radeon™ X1950 series
· ATI Radeon™ X1800 series
· ATI Radeon™ HD 2350 series
· ATI Radeon™ HD 2300 series
· ATI Radeon™ X1650 series
· ATI Radeon™ X1600 series
· ATI Radeon™ X1550 series
· ATI Radeon™ X1300 series

---

### Post by bupe on 2008-11-01
Ok, I'm stuck. I couldn't dig up anything that would help me fix this MultiView problem. Any advice would be much appreciated.

Best,
Peter

---

### Post by bupe on 2008-11-02
I found some more information in the [Catalyst 8.8 release notes]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html"):

> ATI MultiView™

ATI MultiView™ provides the ability to utilize GPUs from multiple adapters on an independent multi-display desktop. It allows a user to configure, manage and use a Multiview configuration under Linux and allows OpenGL applications run on any displays driven by multiple GPUs. ATI MultiView™ provides:

    * Multi-GPU configuration support
    * Up to 4 displays support
    * Enhanced display configuration and selection through the Catalyst Control Center Linux Edition
    * Administrator shortcut which provides access to configuration options that require root privileges. Root privileges are required for multi-screen configurations, including enabling and disabling certain multi-screen configurations and screen placement.
    * ATI MultiView™ only works on systems with two identical FireGL™ products which include:
          o ATI FireGL™ V7700
          o ATI FireGL™ V7400
          o ATI FireGL™ V5600
          o ATI FireGL™ V5200
          o ATI FireGL™ V3700
          o ATI FireGL™ V3600
          o ATI FireGL™ V3400
          o ATI FireGL™ V3350
          o ATI FireGL™ V3300 
    * ATI MultiView™ does not operate with Compiz environments
    * ATI MultiView™ (released in 8.52/8.53) does not operate with Xinerama enabled 

---

### Post by bupe on 2008-11-03
I managed to get 3 out of 4 working buy following this [guide]("http://www.phoronix.com/scan.php?page=article&item=amd_multiview&num=1"). Almost there :)

I also tried Sabayon 3.5, Fedora 9 and openSUSE 11 and got back to Ubuntu 8.0.4 as this one seems to be the most stable (and I couldn't get X started only in Ubuntu and Fedora... :D)

Anyway should anyone have some easy to follow advice on how to properly set this up I'll check back later. I'll also post if I found a final solution - right now I have a fresh Ubuntu install, I'll be more careful this time ;)

---

### Post by bupe on 2008-11-04
I replaced 8.0.4 with a fresh install of 8.10.
This is what I have now:

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	     0	"screen1" 0 0
	Screen		"screen2" LeftOf "screen1"
	Screen		"screen3" LeftOf "screen2"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules" "xorg"
	Option		"XkbModel" "pc105"
	Option		"XkbLayout" "hu"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"VX9x2"
EndSection

Section "Monitor"
	Identifier	"L245WP"
EndSection

Section "Monitor"
	Identifier	"42C3001P"
EndSection

Section "Device"
	Identifier	"HD3870.1"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"DesktopSetup" "horizontal"
	Option		"OverlayOnCRTC2" "1"
EndSection

Section "Device"
	Identifier	"HD3870.2"
	Driver		"fglrx"
	BusID		"PCI:6:0:0"
	Option		"OverlayOnCRTC2" "0"
EndSection

Section "Screen"
	Identifier	"screen1"
	Device		"HD3870.1"
	Monitor		"VX9x2"
	DefaultDepth	24
	SubSection	"Display"
		Depth		24
		Modes		"2560x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen2"
	Device		"HD3870.2"
	Monitor		"L245WP"
	DefaultDepth	24
	SubSection	"Display"
		Depth		24
		Modes		"1920x1200"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"screen3"
	Device		"HD3870.2"
	Monitor		"42C3001P"
	DefaultDepth	24
	SubSection	"Display"
		Depth		24
		Modes		"1366x768"
	EndSubSection
EndSection

Section "Extensions"
	Option	    "Composite" "disable"
EndSection

```

I have big desktop on the two 19" lcds and a separate desktop on the 24". I can't set an individual resolution to the LCD TV...
Major problems:

- cannot move windows between the 2x19" and the 24".
- if composite is enabled then the taskbars do not load...

Any and all help would be much appreciated, I'm starting to give up... I don't want to go back to windows but these are major flows in the operating system...

Thanks,
Peter

---

### Post by alfalfa31 on 2008-11-04
Sorry about not replying.  I got caught up in something else.

As soon as I can devote some time in this, I'll answer...

---

