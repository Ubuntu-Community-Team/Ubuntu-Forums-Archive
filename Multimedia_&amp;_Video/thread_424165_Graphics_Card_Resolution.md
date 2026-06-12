---
title: "Graphics Card Resolution"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by rnichols430 on 2007-04-26
I cannot get above 800x600 for my screen size.  I assume its because of the graphics card isnt installed correctly.  I think what I have in the machine is a Jaton Video -88PCI-16.. Which comes out to a PCI TNT2 Card i think, i googled it.. Where can I find drivers for this for ubuntu 7.04?

---

### Post by reckless2k2 on 2007-04-26
Search the forums on "xorg.conf" editing. That will explain what you have to do to change your resolution. You'll just have to change a line or 2 in that file then reboot and you'll be fine as long as you know what your resolution can max at.

---

### Post by rnichols430 on 2007-04-26
Says in there that I should have more options than what I do on the drop down... Any other ideas?

---

### Post by en3rgy on 2007-04-26
> **reckless2k2 said:**
> Search the forums on "xorg.conf" editing. That will explain what you have to do to change your resolution. You'll just have to change a line or 2 in that file then reboot and you'll be fine as long as you know what your resolution can max at.

That doesn't seem to help unfortunately. I too have tried that... for hours now it seems and still I am also @ 800x600@50hz. There doesn't seem to be a way to fix this for some reason.

---

### Post by reckless2k2 on 2007-04-29
Hey guys, sorry I was away and had hoped that someone else would chime in. I'll give you a quick walk through of what needs to be done. Please make sure you know your max resolutions on your monitors before editing this file and ALWAYS backup the file before editing. Try to make that a rule if you have to muck around with config files at all. 

Open a terminal window:

Applications > Accessories > Terminal

Then type the following:

[COLOR="Blue"]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup[/COLOR]

That step is going to backup the file. Now edit the file by doing this:
[COLOR="Blue"]
sudo gedit /etc/X11/xorg.conf[/COLOR]

This will open gedit to edit the xorg.conf file. You are going to go almost to the bottom of the file to the "screen" section. Where it currently says:

[COLOR="Blue"]Modes     "800x600"[/COLOR]

Change all of them to whatever the recommended resolution it is you are trying to get. Here is an example of mine:

[COLOR="Blue"]Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x1024"
	EndSubSection
EndSection


[/COLOR]

After you've made your changes, save the file and then reboot your machine. Everything should be fine then. I assume you guys are looking for resolutions like 1024x768. 

IF YOU HAVE CRAZY NEW LCD WIDE SCREEN SIZED SCREEN RESOLUTIONS, YOU HAVE TO DO SOMETHING ELSE FIRST. 

Just let me know how it works out for you.

---

### Post by bakeha on 2007-04-29
I have the same problem - Ubuntu does not allow me to use my screen's native resolution of 1280x1024 and restricts me to 1024x768.

I tried changing xorg.conf so that every "mode" line read  Modes "1280x1024" and there were some changes:

[LIST=1]
[*]I now have more options in the screen resolution dialogue, however no choice of 1280x1024
[*]Before logon, the screen res. is too high for the screen - too tall (a little of the top and bottom are off the screen and squashed horizontally.
[/LIST]

Please help.

---

### Post by bakeha on 2007-04-29
I stand corrected!

I went to enable "desktop effects" and ubuntu installed a new graphics driver. When I rebooted I could choose the correct screen res.

Thanks

---

### Post by r2d22 on 2007-05-01
it didn't work for me.

i want rez of 1280x1024. it doesn't show up...

 here's the section of my conf file i changed:

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

### Post by pelikan on 2007-05-01
You need to get rid of all but "1280x1024." If you want to set the refresh rate as well, instead of "1280x1024," put "1280x1024_60" (if 60 Hz is your desired refresh rate).

---

### Post by r2d22 on 2007-05-02
ahh. that's much better, thank you!

---

### Post by DJiNN on 2007-05-03
> **pelikan said:**
> You need to get rid of all but "1280x1024." If you want to set the refresh rate as well, instead of "1280x1024," put "1280x1024_60" (if 60 Hz is your desired refresh rate).

Well, i can't believe that worked incredibly well & really easily! :) Thanks for the tip. I'll be sure to pass it on whenever i see someone else with the same problem (Which seems to be happening quite a lot!) :)

Thanks again.......

DJiNN

---

### Post by montonec on 2007-05-03
I have the same problem... I tried editing xorg.conf, but, to my surprise, the value in the file is the correct one, that is 1440x900, whike I can't get a reolution better than 1024x768... Anyone could help? Tanks so much!
PS: I copy my configuration below:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Option		"XkbLayout"	"es"
	Option		"XkbVariant"	"cat"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by pelikan on 2007-05-03
Try changing DefaultDepth to 24 (it's 16 now).
Then delete all SubSection "Display" values except for:
SubSection "Display"
Depth 24
Modes "1440x900"
EndSubSection

That section will look like this:
Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1440x900"
EndSubSection

---

### Post by montonec on 2007-05-04
Thanks Pelikan, but I've followed your suggestions and still doesn't work... i edited the file as you said, but I still don't get any higher resolution than 1024x768... Any other tip? Thanks!

---

### Post by pelikan on 2007-05-04
That's all I've got. Hopefully someone more knowledgeable will be able to solve this one.

---

### Post by SkinR on 2007-05-04
I would like to Thank You very much for the info!

I have been having problems changing my res from 1024x768,
But after i read the info you provided i am now running 1680x1050.

I can not thank you enough!

SkinR

---

### Post by foosa on 2007-05-05
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
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
	Identifier	"nVidia Corporation G71 [GeForce 7900 GT/GTO]"
	Driver		"nvidia"
	Busid		"PCI:6:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-51
	Vertrefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7900 GT/GTO]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"1680x1050"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"1680x1050"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"1680x1050"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"1680x1050"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"1680x1050"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"1680x1050"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

I followed what everybody said, but still can't get 1680X1050.  Any ideas?

---

### Post by foosa on 2007-05-05
ok, I got it at 1680X1050, but it extend outside of my moniter.  20.1 widescreen and that is the rec. resolution for it.  Any ideas?

---

### Post by DJiNN on 2007-05-05
> **foosa said:**
> ok, I got it at 1680X1050, but it extend outside of my moniter.  20.1 widescreen and that is the rec. resolution for it.  Any ideas?

LCD or CRT monitor? If it's LCD you should have auto adjust, try that.

Also, are you using nVidia drivers? If so, fire up the nVidia control panel.... there's ususally a load of stuff in there that you can try. 

DJiNN

---

### Post by DJiNN on 2007-05-05
> **montonec said:**
> Thanks Pelikan, but I've followed your suggestions and still doesn't work... i edited the file as you said, but I still don't get any higher resolution than 1024x768... Any other tip? Thanks!

Did you get it working after all?  If not, did you try what the previous poster said, about putting the Res that you want (1440x900) and then the refresh rate directly after it...... Like this.

Modes  "1440x900_60" 

Obviously change the "60" part to whatever refresh rate your monitor can handle - on mine it's 75. 

It worked well for me on a couple of machines....... Let me know how you get on.

DJiNN

---

### Post by DJiNN on 2007-05-05
> **foosa said:**
> I followed what everybody said, but still can't get 1680X1050.  Any ideas?

It's only a guess here, because i'm not 100% sure, but you have your modes messed up. I'm assuming that they need to be in order?

You have the 1024x768 one before the 1680x1050!! It should be the other way round, like this.........

Modes    "1680x1050" "1280x1024" "1024x768"  

From the highest down to the lowest, do you see? 

try changing them around & see what happens....... Let me know how it goes?

Cheers.........

DJiNN

---

### Post by foosa on 2007-05-06
> **DJiNN said:**
> It's only a guess here, because i'm not 100% sure, but you have your modes messed up. I'm assuming that they need to be in order?

You have the 1024x768 one before the 1680x1050!! It should be the other way round, like this.........

Modes    "1680x1050" "1280x1024" "1024x768"  

From the highest down to the lowest, do you see? 

try changing them around & see what happens....... Let me know how it goes?

Cheers.........

DJiNN


I just did that, now I can't see anything.  I get out of bounds, or something along those lines, from my monitor.  Everything still works, I just can see.  I can log in(type user name and password and hear the sounds)  but its all black.  how can I fix this?

---

### Post by DJiNN on 2007-05-06
> **foosa said:**
> I just did that, now I can't see anything.  I get out of bounds, or something along those lines, from my monitor.  Everything still works, I just can see.  I can log in(type user name and password and hear the sounds)  but its all black.  how can I fix this?

The first thing you do is put it back the way that you found it. :) So if you have changed the order then put them back again. :) 

 	Code:
 	sudo dpkg-reconfigure -phigh  xserver-xorg 
Have you tried the above yet? Bring up a Terminal then after you have run the xorg config, CTRL-ALT-BACKSPACE to reset X and log in again & see what happens.

Also, have you done any detective work on your monitor and/or video card, to see what the vertical & horizontal sync rates are, or the highest res?

What monitor & card are you using, and what flavour & release of Ubuntu are you running?

DJiNN

---

### Post by foosa on 2007-05-06
> **DJiNN said:**
> The first thing you do is put it back the way that you found it. :) So if you have changed the order then put them back again. :) 


I would, but all I can see is black.  After the Ubuntu loading screen it goes black and I can't see anything.  I can hear the log in drums but no picture.

---

### Post by Spadje on 2007-05-06
When I try to edit that file It tells me that I cannot becuase I am not the owner of the file. Sorry but I am new to linux and am loving it but it just doesnt support my new Samsung 206BW...... 1680x1050_60 is what I want to add....thanks for any help. 

Spadje

---

### Post by LaRoza on 2007-05-09
[solved]

I have a similar problem with resolution, I am not at my computer so I can not try things immediately.

I tried edition xorg.conf, deleting all the resolutions I didn't want, but I still did not get any results. I did not yet try deleting other subsections.

If someone spots a solution by looking at the xorg.conf, please tell me, this copy doesn't have the other resolutions deleted.

Thanks

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
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
	Identifier	"nVidia Corporation C51 [GeForce 6150 LE]"
	Driver		"nv"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation C51 [GeForce 6150 LE]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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



```

---

