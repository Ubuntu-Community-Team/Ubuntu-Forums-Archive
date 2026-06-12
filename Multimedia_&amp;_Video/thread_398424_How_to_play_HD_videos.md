---
title: "How to play HD videos?"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by G-Izzat on 2007-04-01
Hey,guys.

I just downloaded the hd trailer of Grand Theft Auto IV,which is 1280x720.

I tried playing it but the media player keeps on closing itself right after clicking on the video.

How can I play it?

> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)


---

### Post by crispy_420 on 2007-04-03
Sounds like a missing video codec to me. Could you post a link to the download? Do you know the format it is in?

---

### Post by Splat on 2007-04-03
Might want to try VLC. It plays nearly all forms of media without having to worry about codecs at all. I think you can install the latest version through the Add/Remove applications feature by simply searching for vlc.

---

### Post by G-Izzat on 2007-04-04
> **crispy_420 said:**
> Sounds like a missing video codec to me. Could you post a link to the download? Do you know the format it is in?

It's a .wmv file. Downloaded it from gametrailers.com  

[Link here]("http://download.gametrailers.com/gt_vault/t_gta4_debut_h264.wmv")
> 
Dimensions : 1280 x 720
Codec : Microsoft Windows Media 9
Framerate : 5 frames per second
Bitrate : N/A

Audio
Bitrate : N/A
Codec : WMA Version 8
Sample rate : 48000 Hz
Channels : 2


Tried playing it with MPlayer,VLC and the default Ubuntu player. Everytime I tried to open the video, the player will start and just exit itself.

---

### Post by Jeroen Vernooij on 2007-04-04
Same problem here, with the same graphics card.. I think the driver is broken, because the card is powerful enough (it plays the HD videos very well in windows..)
Haven't been able to solve this (haven't tried many things) :(

---

### Post by crispy_420 on 2007-04-05
I just downloaded it and gave it try and it worked for me. I have mplayer setup as default player for windows media formats. You do have the win32 codecs installed?

---

### Post by Jeroen Vernooij on 2007-04-05
> **crispy_420 said:**
> I just downloaded it and gave it try and it worked for me. I have mplayer setup as default player for windows media formats. You do have the win32 codecs installed?

You most probably have a dedicated videocard (nVidia / ATi)
On Intel this doesn't work, which sucks big time :( 
I have tens of High definition videos

---

### Post by G-Izzat on 2007-04-05
Hopefully there's a solution for this.
I think I've heard from somewhere that they are able to play the videos with no problem at all using the Intel Graphic Card.
I'm using the Sony Vaio SZ43 by the way,which also have the Nvidia Geforce Go 7400 but you have to slide the switch to change the graphic card.

---

### Post by crispy_420 on 2007-04-05
Infact I do have an ATI card. But I'll give it try tonight on my laptop, it has onboard VIA video at only 64MB shared for memory.

Have you set up your Intel driver?

---

### Post by G-Izzat on 2007-04-05
Yeah,already set it up.
Right now if I try to play it using Mplayer,it will play only for 5 seconds,then the video will stop.

---

### Post by NooneReally on 2007-04-05
I had the same problem and added the following line to my xorg.conf in the Device section where i810 is located:

```
        Option          "CacheLines"            "1024"
```

fixed all my HD vid problems.

---

### Post by radioouman on 2007-04-05
> **NooneReally said:**
> I had the same problem and added the following line to my xorg.conf in the Device section where i810 is located:

```
        Option          "CacheLines"            "1024"
```

fixed all my HD vid problems.

Need to set that to the max number of vertical lines in your video file.  A 1080i file needs 1920 vertical lines.

---

### Post by crispy_420 on 2007-04-05
Ok I tried it on my laptop and it worked fine. Mplayer did fill my entire screen but it played fine. Keep in mind mine is a VIA chipset not Intel. So it sounds like a Intel video driver issue to me.

---

### Post by G-Izzat on 2007-04-06
> **radioouman said:**
> Need to set that to the max number of vertical lines in your video file.  A 1080i file needs 1920 vertical lines.

Tried that too. But it still won't work.
Hmm, seems like it'll be quite some time before I can try to play all these videos.

---

### Post by loko on 2007-04-06
hello,

in the 	Section "Device", enter the following in your xorg.conf

Option		"LinearAlloc"		"6144"

now the video should work!


```
Section "Device"
	Identifier	"Intel 950GM"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"XAANoOffscreenPixmaps"	"true"
	Option          "TripleBuffer" "true"
	Option		"LinearAlloc"		"6144"
EndSection
```

---

### Post by G-Izzat on 2007-04-06
> **loko said:**
> hello,

in the 	Section "Device", enter the following in your xorg.conf

Option		"LinearAlloc"		"6144"

now the video should work!


```
Section "Device"
	Identifier	"Intel 950GM"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option		"XAANoOffscreenPixmaps"	"true"
	Option          "TripleBuffer" "true"
	Option		"LinearAlloc"		"6144"
EndSection
```

Damn,this is not good. I added the linear alloc to my xorg.conf. It only played for around 3 seconds and then the video just stop.
I wonder,is my driver good enough to play this kind of videos?
It should be right? Since I can play it on Vista normally.

---

### Post by loko on 2007-04-07
i also have intel 945GM,

the video playes like it should till the end - without problems.

so, what ubuntu do you use, feisty or edgy?

also post your xorg.conf

and

post the result of ```
glxinfo | grep direct
```

---

### Post by Jeroen Vernooij on 2007-04-07
On my 945GM, NooneReally's solution resolved it! (with 1280 instead of 1024)

Thank you so much!!! :KS :KS :KS 


But I really hope in the future this stays possible, as with xorg 7.3 xorg.conf will be removed :confused:

---

### Post by G-Izzat on 2007-04-07
> **loko said:**
> i also have intel 945GM,

the video playes like it should till the end - without problems.

so, what ubuntu do you use, feisty or edgy?

also post your xorg.conf

and

post the result of ```
glxinfo | grep direct
```

I'm right now using Feisty. The latest kernel which is -14 I think.

glxinfo | grep direct
> izzat@Izzat:~$ glxinfo | grep direct
direct rendering: Yes


My xorg.conf
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
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option		"LinearAlloc"		"6144"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
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

