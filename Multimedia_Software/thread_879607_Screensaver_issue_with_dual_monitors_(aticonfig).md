---
title: "Screensaver issue with dual monitors (aticonfig)"
date: 2008-08-04
forum: Multimedia Software
---

### Post by BWPanda on 2008-08-04
I've got two monitors running off my dual-DVI ATI card and setup with aticonfig - all seems to be working well.

However, when the screensaver comes on, the main screen goes black with just the mouse pointer showing and the second screen stays showing the desktop. When I try to get back to the desktop on the main screen by moving the mouse, nothing happens. The mouse moves around and can move to the second screen, but can't click on anything. I have to Ctrl-Alt-Backspace and login again.

Any ideas why this happens and how to fix it?

---

### Post by trevinoj on 2008-11-30
I'm having the same problem, with dual ati monitors
here's my xorg.conf settings

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	Screen         "aticonfig-Screen[1]" Leftof "Default Screen"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
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

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

---

### Post by BWPanda on 2008-12-01
I ended up just disabling my screensaver... Never did find a fix.

---

### Post by Person98 on 2008-12-04
I had a similar issue to you guys, i believe it is due to the fact 3D rendering doesn't work with multiple monitors (the resolution is too hight) there are work arounds to this i have seen, but for my i just selected a screensaver that isn't 3D, give the blank screen a go, or else you could try a different screensaver then the default, i forget which one i used but i have no more issues with it hope this helps

---

### Post by CHaoSlayeR on 2008-12-04
Hi guys,

well I have dual-head setup too and all screensavers work fine for me (also the 3D ones). I have full 3D acceleration on both monitors.

However I think the main issue here might be that the dual-head setup has to be the "BigDesktop" mode and not only two separate screens (at least I can see that in the xorg.conf provided by trevinoj). So here I provide my xorg.conf which can be adapted to create your own xorg.conf. Please be aware that I am using the same resolutions for both monitors and I use CRTs, not LCDs so you have to change a lot. But in basic you should only have **one** device section and **one** screen section:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Logitech Dual Action"
EndSection

Section "Files"
EndSection

Section "Module"
#	Load  "bitmap"
#	Load  "ddc"
	Load  "vbe"
#	Load  "i2c"
	Load  "extmod"
	Load  "GLcore"
	Load  "dbe"
#	Load  "v4l"
	Load  "freetype"
#	Load  "int10"
	Load  "glx"
	Load  "dri"
	Load  "drm"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "de"
	Option	    "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Logitech Dual Action"
	Driver      "joystick"
	Option	    "Device" "/dev/input/js0"
	Option	    "SendCoreEvents" "true"
	Option	    "MapAxis1" "mode=relative axis=+1.5X deadzone=30"
	Option	    "MapAxis2" "mode=relative axis=+1.5Y deadzone=30"
	Option	    "MapButton2" "key=57"
EndSection

Section "Monitor"
#	Option	    "VendorName" "Sampo"
#	Option	    "ModelName" "AlphaScan 871"
	Identifier   "Monitor0"
	HorizSync    27.0 - 100.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
#	Option	    "VendorName" "Iiyama"
#	Option	    "ModelName" "Vision Master 450"
	Identifier   "Monitor1"
	HorizSync    27.0 - 102.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS" "true"
EndSection

Section "Device"
#	Option	    "AccelMethod" 		"EXA"
#	Option	    "AddARGBGLXVisuals" 	"true"
#	Option	    "AllowGLXWithComposite" 	"true"
#	Option	    "Mode2" 			"1280x1024" #Resolution for second monitor
#	Option	    "mtrr" 			"no" # disable DRI mtrr mapper, driver has its own code for mtrr!
#	Option	    "no_accel" 			"no"
#	Option	    "no_dri" 			"no"
#	Option	    "XaaNoOffscreenPixmaps" 	"true" # unsupported as of 8.10
#	Option	    "BlockSignalsOnLock" "on"
#	Option	    "DRI" "true"
#	Option	    "ForceGenericCPU" "off"
#	Option	    "KernelModuleParm" "locked-userpages=0"
#	Option	    "MigrationHeuristic" 	"greedy"
#	Option	    "RenderAccel" "true" # unsupported as of 8.10
	Identifier  "Device0"
	Driver      "fglrx"
	BoardName   "ATI Radeon HD2400 Pro"
	Option	    "BackingStore" "on"
#	Option	    "EnablePrivateBackZ" 	"yes" #Enable 3d support <= May Not Work
	Option	    "UseFastTLS" "1" # 0 -> Fast, 1 -> Faster, 2 -> Compatible (WINE)
	Option	    "OpenGLOverlay" "off"
	Option	    "TexturedVideo" "on"
	Option	    "TexturedVideoSync" "on"
	Option	    "VideoOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
#	Option	    "DPMS"
	Option	    "EnableMonitor" "crt1,crt2"
#	Option	    "EnablePageFlip" 		"true"
	Option	    "HSync2" "27.0 - 102.0" #This sets the horizontal sync for the secondary display.
	Option	    "PairModes" "1280x1024+1280x1024"
	Option	    "Textured2D" "on"
	Option	    "VRefresh2" "50.0 - 160.0" #This sets the refresh rate of the secondary display.
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Device0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1280x1024"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

Currently I'm using driver 8.10 and especially the driver options other than **"VRefresh2"**, **"HSync2"**, **"EnableMonitor"** and **"DesktopSetup"** are not what you have to configure to get DRI and/or xv to work correctly for your system.

Hope I can help out a bit, although I'm not that deep into linux as a lot of others here.

Greetz,

C]-[aoZ

---

### Post by Person98 on 2008-12-09
just curious chaoz, do you have 3D rendering on the full desktop, because when ever i tried to get it going it would only render up to 2048 in the horizontal direction, but that was a while ago and i haven't tried recently. just wondering if it was worth another shot

thanks

---

### Post by CHaoSlayeR on 2008-12-10
@Person98:

It may be an internal limitation of the card itself when it doesn't support OpenGL beyond 2048 pixels in width. I don't know what my HD2400 card has as a limitation for that but hey, I just got it working.

I really struggled a lot with the fglrx driver but I finally got it. I don't use compiz or such things. Never tried that out but I have AIGLX enabled and in the Xorg.0.log there are the following statements:
```

(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0

```

And as I have transparent windows and shadows activated in KDE3 I suspect that I have full hardware 3D acceleration for the complete desktop. I think in the fglrx configuration the main point is to only define one screen for the whole desktop. All the other things like xinerama aso. should be done automatically.

So if you have a radeon HDxxxx I would give it a try.


Regards,

C]-[aoZ

---

### Post by markbuntu on 2008-12-10
You should be using the Catalyst Control Center to setup the big desktop and aticonfig for doing any particular setting like different screen sizes etc that is not in the CCC yet.

aticonfig --help

will give you the list of options for all that. 

I set up my big desktop with CCC and have no problems except for the flickering windowed video which will be fixed with dri2 which will be included in Xorg7.5/xserver1.6  which will be out soon. xorg.conf is being deprecated so do not depend on using it for much longer.

---

### Post by CHaoSlayeR on 2008-12-10
Well, with every new driver release I'm trying out to reconfigure the setup using CCC and aticonfig (resetting the xorg.conf completely before that). And every time it makes some other mistakes. Either it uses an incompatible modeline for my CRTs so that I can't see anything except flickering displaced lines or it always uses 60 Hz without giving me the ability to change that or it just deosn't work at all resulting in a low graphics mode.

If it works for you I'm glad to hear that, otherwise I wouldn't dare ATI's developers much. But it just didn't work for me so far.

So every time I'm stuck at modifying my previously handmade xorg.conf and afterwards applying the changes to AMD's internal configuration file using 
```
aticonfig --input=[handmade.xorg.conf]
```

Some time and driver versions ago I also had that flickering video issue but I'm not that sort of guy that just lives with that when I can see others that got it working. So I am always into xorg.conf modification again. With nearly each driver version from scratch to figure out what behavior has changed, what has made better and what has gone worse.

The next thing I don't like is that ATI/AMD doesn't provide a list of supported driver options (they can always make the note that configuring **should** be done with at least the aticonfig command).

I really hope that DRI2 will make life much easier but how does it change the way the basic display configuration is done? Isn't DRI just for the hardware acceleration part? All the other things like chosing the resolution, screen setup, modelines for the connected display aso. is done completely outside of that or am I missing something there?


Greetz,

C]-[aoZ

---

### Post by markbuntu on 2008-12-10
Dri2 will just fix the windowed flickering problem. It allows hardware acceleration in independent windows. Everything else will eventually be in the CCC. 

It is a difficult situation for the ati devs, having so much catching up to do while adding in all the new stuff and new cards and features at the same time without breaking things on a monthly release schedule. It has basically been a mad scramble for them since AMD bought ATI and put a fire under their *** to get the linux drivers up to par. I expect by next year this time the ati drivers will be dialed in and the CCC will be what it is supposed to be. Meanwhile we must bear with this work in progress.

You can talk to the ati devs in the Phoronix forums, there is a talk to the devs thread. Tell them what you need or would like.

---

### Post by CHaoSlayeR on 2008-12-10
OK, I'll then head over to the ATI devs with my specific problem posted on another thread here. Maybe they know what's going wrong.

It was absolutely neccessary that AMD put ATI's devs under fire regarding the linux support. In the future more and more people will be using non-M$ operating systems and it wouldn't be whise to ignore that fact. But that's another story.

Regarding your flickering video have you tried it with video out set to "gl:yuv=3"? For me it was the only option that worked smooth with excelent hardware acceleration and scaling (just "gl" gave me a very blocky and non-accelerated ouput).

---

### Post by markbuntu on 2008-12-10
I only have the problem with compiz running and I can live without that when I want to watch a video. I played with aticonfig for a while and xorg.conf and what I found with some of the older drivers like 8.6 through 8.8 was that TexturedVideo "off" worked. But I don't even bother with that anymore, I just turn off the destop effects.

Compiz is nice but not a critical part of my linux experience. 

Just for a little perspective, the first time I used linux was in the mid 1990s. If you could get x up and running without catching your monitor on fire it was considered a success. It could do things even back then that windows people could only dream about and I find that that is still the case.

Then I drifted away for about a decade and I come back and it is just totally amazing at the progress that has been made and is ongoing so I am willing to just let it all unfold and enjoy what I get.

The only thing that bugs me is the need to still use terminal.....what's up with that?

---

### Post by CHaoSlayeR on 2008-12-10
I switched all of my computers at home to non-M$ operating systems about one year ago. Two of them with Ubuntu and on the server runs OpenSolaris.

As it was my first experience at all with Linux as a full desktop system it was rather hard to get all things working as expected the first time. And especially regarding to things like X / DRI configuration there is nothing better than the xorg.conf itself. I just had to learn the hard way how those things work together and I'm still missing a lot of things and don't understand everything.

And so the console is my best friend because I can reconfigure things on the computer of my girl friend while she uses it. I really love SSH and hate M$ for not including such.

In the company I work in we have a linux freak there that just let one of the servers run the X for him, because the laptop he uses just won't give him the performance he needs. Remote X. One of the many many cool things linux/unix is capable of.

However I would also like it if linux would get more GUI support for the administrative tasks. The tools that are available are only dealing with subsets or special interests that some module is capable of. E.g. I know of no graphical utility that you can use to configure the X server as you would be able to by editing the xorg.conf manually.

Also the auto detection of configuration options for a device needs to be much better.

---

