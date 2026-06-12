---
title: "Pimp my xorg.conf ---&gt; ati x1650 and 3d games"
date: 2008-05-03
forum: Multimedia Software
---

### Post by |{urse on 2008-05-03
hi there, when i run the game nexuiz, it looks like this

[http://i295.photobucket.com/albums/mm132/UsernameKurse/nexuiz000000.jpg](http://i295.photobucket.com/albums/mm132/UsernameKurse/nexuiz000000.jpg)

the output 

```
Nexuiz Linux 15:50:35 Apr  8 2008
Trying to load library... "libz.so.1" - loaded.
Added packfile /usr/share/games/nexuiz/data/data20080229.pk3 (3982 files)
Trying to load library... "libcurl.so.4" - loaded.
Failed to init SDL joystick subsystem: 
Trying to load library... "libvorbis.so.0" - loaded.
Trying to load library... "libvorbisfile.so.3" - loaded.
Trying to load library... "libmodplug.so.0" - loaded.
Trying to load library... "libOffscreenGecko.so" "/usr/lib/games/nexuiz/libOffscreenGecko.so" - failed.
execing quake.rc
execing default.cfg
execing physicsQBR.cfg
execing newhook.cfg
execing weapons.cfg
execing normal.cfg
execing config.cfg
couldn't exec data/campaign.cfg
couldn't exec autoexec.cfg
Initializing Video Mode: fullscreen 1024x768x32x60hz
Linked against SDL version 1.2.11
Using SDL library version 1.2.11
0 SDL joystick(s) found:
Trying to load library... "libjpeg.so.62" - loaded.
Trying to load library... "libpng12.so.0" - loaded.
Draw_CachePic: failed to load gfx/complete
Draw_CachePic: failed to load gfx/inter
Shader 'textures/Reaptxt/sun' already defined

```

and then goes on to try to autodetect sound etc.

The game runs but hideously!

here is my xorg.conf beginning with the device section

```


Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Novatek 563"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Novatek 563"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
        Load		"dri"
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection
Section "DRI"
    Group       0
    Mode        0666
EndSection
```

any ideas? thx in advance.

---

### Post by |{urse on 2008-05-04
anyone?


now my xorg.conf looks like this
```

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
	Option		"XaaNoOffscreenPixmaps"	"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"EnablePageFlip"	"true"
	Option		"AccelMethod"	"EXA"
	Option		"MigrationHeuristic"	"greedy"
	Option		"DRI"	"true"
	Option		"TexturedVideo"	"on"
	Option		"UseFastTLS"	"0"
	Option		"BlockSignalsOnLock"	"on"
	Option		"KernelModuleParm"	"locked-userpages=0"
	Option		"ForceGenericCPU"	"off"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Novatek 563"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Novatek 563"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"dri"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"false" #<---- i dont want to resort to it 
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection
```

textures are showing up correctly in nexuiz but the gameplay is so ridiculously slow that its not worth playing at all.

oh and now glxgears crashes x completely! lol

funny thing is compiz has never run better.

I installed the latest ati drivers but fglrx-info says this

```
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

```

wth mesa? I thought i was using the new ati stuff?

I am thouroughly demused. Pls help! :(

---

### Post by WalmartSniperLX on 2008-05-04
> **|{urse said:**
> anyone?


now my xorg.conf looks like this
```

Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
	Option		"XaaNoOffscreenPixmaps"	"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"EnablePageFlip"	"true"
	Option		"AccelMethod"	"EXA"
	Option		"MigrationHeuristic"	"greedy"
	Option		"DRI"	"true"
	Option		"TexturedVideo"	"on"
	Option		"UseFastTLS"	"0"
	Option		"BlockSignalsOnLock"	"on"
	Option		"KernelModuleParm"	"locked-userpages=0"
	Option		"ForceGenericCPU"	"off"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Monitor"
	Identifier	"Novatek 563"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc ATI Default Card"
	Monitor		"Novatek 563"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"	"640x350"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
	Load		"dri"
EndSection
Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"false" #<---- i dont want to resort to it 
EndSection

Section "DRI"
	Group	0
	Mode	0666
EndSection
```

textures are showing up correctly in nexuiz but the gameplay is so ridiculously slow that its not worth playing at all.

oh and now glxgears crashes x completely! lol

funny thing is compiz has never run better.

I installed the latest ati drivers but fglrx-info says this

```
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

```

wth mesa? I thought i was using the new ati stuff?

I am thouroughly demused. Pls help! :(

Just wondering. What method of installing the ATI drivers did you use? Did you get them from the repos or did you download it from the ATI website?

---

### Post by WalmartSniperLX on 2008-05-04
This is a shot in the dark. Try moving your "module" section up so that its the first section in the xorg.conf file. Honestly I don't know how xorg.conf is read, but if it's read like any normal shell script, then it may be important to have it laid out in a certain format or order. After moving the module section, do a ctrl-alt backspace to start x.

---

### Post by |{urse on 2008-05-04
just tried the method described above and x failed to start. *shrugs* thx for the idea though. have everything back to the way it was before again.

GOD this is frustrating lol. sauerbraten, nexuiz, tremulous etc are horridly slow.

oh and i downloaded the latest catalyst from ati's site, then i blocked the preinstalled fglrx from starting up with

sudo gedit /etc/default/linux-restricted-modules-common

and manually edited xorg.conf.

I know this is in the topic but just a reminder, this is an x1950 256mb (liquid-cooled ffs) theres nothing wrong with the card, verified this @ work on a fc8 machine.

---

### Post by WalmartSniperLX on 2008-05-04
> **|{urse said:**
> just tried the method described above and x failed to start. *shrugs* thx for the idea though. have everything back to the way it was before again.

GOD this is frustrating lol. sauerbraten, nexuiz, tremulous etc are horridly slow.

oh and i downloaded the latest catalyst from ati's site, then i blocked the preinstalled fglrx from starting up with

sudo gedit /etc/default/linux-restricted-modules-common

and manually edited xorg.conf.

I know this is in the topic but just a reminder, this is an x1950 256mb (liquid-cooled ffs) theres nothing wrong with the card, verified this @ work on a fc8 machine.

That's strange. I just recently downloaded drivers from ati and installed them and my hd2600pro works fine. You did build the .deb packages instead of the automatic installer right? 

I also just migrated back from F8 and I had more stable graphics performance in general in F8.

---

### Post by |{urse on 2008-05-05
yeah i sure did, followed the wiki as well. And direct rendering..

> kurse@kurse-desktop:~$ DISPLAY=:0 glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Radeon X1650 Series


---

### Post by ppeetteerr on 2008-05-05
If you have xorg 7.3 you may not need an xorg.conf try moving it to a new directory and restarting X.  I have the same card and just installed the drivers and started X

Running hardy

---

### Post by VitalBodies on 2008-05-05
Install: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

This guide tell you about the Mesa. If you have that showing up the drivers are loaded wrong if you are trying to use ATI proprietary drivers. 

fglrxinfo
Run this command and you should not see mesa...

---

### Post by |{urse on 2008-05-05
yeah thats the exact guide i followed, 3 times to the letter. I have even done a wipe and reload. fglrxinfo is still telling me it's mesa.

---

### Post by |{urse on 2008-05-05
> **ppeetteerr said:**
> If you have xorg 7.3 you may not need an xorg.conf try moving it to a new directory and restarting X.  I have the same card and just installed the drivers and started X

Running hardy

Interesting. I'll try that when i get home. I'm at work atm. To tell you the truth I don't see how that's possible but at this point lol not much would surprise me.

---

### Post by |{urse on 2008-05-05
nope, had to move it back to get a gui init 5 =\

heres my most recent xorg.conf

Compiz is omfg fast but still no 3d gaming.

```
Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
	Load  "dri"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "false"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/input/wacom"
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

```

I'm going to delete the part that says:

> Section "ServerFlags"
	Option	    "AIGLX" "false"
EndSection

and restart X. :neutral:

and it did nothing which i figured it wouldnt as i'm not using aiglx.

---

### Post by |{urse on 2008-05-05
Oh and just to recap. I cant even open catalyst control center which says the driver isn't installed (even though it is) whenever i run glxgears the system halts, and whenever i try to logout now the system halts. This problem has been reproduced 3 times on the same HW configuration and driver was installed each time using instructions from the wiki.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide) <-- this'n

---

### Post by Torgas Prim on 2008-05-05
At least he can get fglrx showing in xorg :(

---

### Post by features on 2008-05-05
I think the problem may be in this section of your xorg.conf...

```
Section "Device"
	Identifier	"ATI Technologies Inc ATI Default Card"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
	Option		"XaaNoOffscreenPixmaps"	"true"
	Option		"AddARGBGLXVisuals"	"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"EnablePageFlip"	"true"
	Option		"AccelMethod"	"EXA"
	Option		"MigrationHeuristic"	"greedy"
	Option		"DRI"	"true"
	Option		"TexturedVideo"	"on"
	Option		"UseFastTLS"	"0"
	Option		"BlockSignalsOnLock"	"on"
	Option		"KernelModuleParm"	"locked-userpages=0"
	Option		"ForceGenericCPU"	"off"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

```

AFAIK, you can only have one overlay method on.  You've got VideoOverlay and TexturedVideo on .. try turning Video Overlay off, since TexturedVideo is intended for the newer ATI cards :)  Here is mine for reference - it's an X1300 Mobility...ignore all the stuff for dual-head.

```
Section "Device"
	Identifier	"ATI Graphics Adapter 0"
	Driver		"fglrx"
	Option		"VideoOverlay"	"off	"
	Option		"OpenGLOverlay"	"off"
	Option 		"TexturedVideo" "on"
	Option		"EnablePrivateBackZ"	"yes"
	Option		"UseInternalAGPGART"	"no"
	Option 		"XAANoOffscreenPixmaps" "on" 
	Option 		"UseFastTLS" "1" 
	Option 		"BackingStore" "on" 
	#dual head Option		"DesktopSetup"	"horizontal"
	#dual head Option		"HSync2"	"64"
	#dual head Option		"VRefresh2"	"60"
	#dual head Option		"Mode2"	"1280x1024"
	#dual head Option		"PairModes"	"1280x800+1280x1024"
	#NOT USED	Option		"MonitorLayout"	"LVDS,AUTO"
	Busid		"PCI:1:0:0"
EndSection


```

And I second the bit about going to [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")  and following the troubleshooting info there.

Hope this helps!

---

### Post by |{urse on 2008-05-05
lol my xorg.conf has changed 3 times since that post. and my posts above stated that was the exact guide i used each time. Thanks for the replies though. 

now check this out! 
I got hella p.o.ed and did exactly what i was told not to bother trying. installed hardy instead of gutsy

> kurse@kurse-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7415 Release

!! NO MORE MESA THANK BAWDo
and...
> 27392 frames in 5.0 seconds = 5478.215 FPS
27404 frames in 5.0 seconds = 5480.686 FPS
26826 frames in 5.0 seconds = 5365.080 FPS
23746 frames in 5.0 seconds = 4749.166 FPS
22848 frames in 5.0 seconds = 4569.472 FPS
26758 frames in 5.0 seconds = 5351.540 FPS

!!!!
Diagnosis: HARDY <3's ATI

I'll have nexuiz installerated in a minute here.
Thanks everyone for your thoughts and for giving me the same link i was already using 5 times! lol j/k but thank you. Hopefully this helps someone.

EDIT: In hindsight i think this may have something to do with my buggy sk8n mobo. My ati card wont even display the bios splash correctly due to its nforce chipset. Iunno.

---

### Post by features on 2008-05-06
lol yeah, rank forum blindness on my part there :D  Glad you got it sorted :)

---

