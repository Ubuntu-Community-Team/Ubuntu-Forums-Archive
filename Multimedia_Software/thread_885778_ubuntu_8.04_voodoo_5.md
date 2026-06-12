---
title: "ubuntu 8.04 voodoo 5"
date: 2008-08-10
forum: Multimedia Software
---

### Post by Kusho on 2008-08-10
Okay, I hope I'm asking this in the right forum.  p2 with a 550 processor running ubuntu 8.04.  voodoo 5500 video card...  and can't get it to display better than 800/600.  Found [http://ubuntuforums.org/archive/index.php/t-18106.html](http://ubuntuforums.org/archive/index.php/t-18106.html) and [http://dri.sourceforge.net/doc/DRIuserguide.html](http://dri.sourceforge.net/doc/DRIuserguide.html) as a few possible solves.  First one seems to be the best, but wrote for a voodoo3, so since i am editing core files, wouldn't there be differences for my board.  And do I need to add packages first to get this to work?  I tried the synaptic package manager for XFree86 and tdfx, but not finding either as a stand alone package.  Do I already have these in 8.04 build??  Do they not work?  Xfree86 sounds like what i want as it actually lists the video card i'm wanting to directly support.

have a 3drage that came with this pc, and get better graphics with that board, but the voodoo 5500 is a monster, and would like to use it vs putting it on a shelf.  no other rigs to run it in right now, and decided to get this box running ubuntu as kind of a test box to see if i like it.  changing over from ME on this rig, as a older gaming rig...  (played dark forces 2, ff7 and a few others well...  but got those running on my main vista and xp rigs, so thought i'd start down the ubuntu path, but wanted it with a rig that i don't HAVE to have running perfectly as every other time I try this os, seems like there a learning curve that you need to read 8000 forums to get past.  Anyway, that all said...  I am trying before I post...  but help would be appreciated.  Any way to get this voodoo 5500 running in better resolutions, or do i have to go back to my shitty 3drage to get decent resolutions?

thanks.

---

### Post by Kusho on 2008-08-10
oh and i tried editing my xorg.conf as previous link says to do but it says In section "Screen" Change defaultdepth value to 16.  There isn't a Default Depth entry.  Also says and for the display, and for the code...  again...  not seeing those entries.  Do I just add them?  Then says SubSection "Display"
Depth 16
Modes "1024x768" 832x600 " "720x400" "640x480"
EndSubSection

There is no Display Entry.  Do I just throw this into the file??

---

### Post by 1337 on 2008-08-10
Hello, first of all I'm happy to meet 3dfx user there are not many of them these days as I'm ex-voodoo user myself years ago and I have much sentiment for that hardware I will try to help you with your problem.

First of all make sure that in your xorg.conf you got:

```

[COLOR="Red"]in[/COLOR] Section "Device"
	
	Driver		"tdfx"  

[COLOR="Red"]in [/COLOR]Section "Screen" 

Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection

[COLOR="Red"]Yes add them if there are not there but make sure that you are adding them in the right 
section, section names above.[/COLOR]

```

That should do the trick for the 3d mode, if you want to use 3d mode you must install from apt or synaptic libglide2 and libglide3 as far I know. I hope it helps feedback me with info if this worked. Long live 3dfx ! :D

Regards

---

### Post by Kusho on 2008-08-10
Okay newb question.

Could not save the file /etc/X11/xorg.conf

You do not have the permissions necessary to save the file....

And this was with gedit from the Applications menu...  do i need to change this file a different way???  I tried to pull up a console and type in the "sudo -i" but just guessing that is just for commands in the console.  ;)  Sure if i play enough I'll answer this one myself....

---

### Post by 1337 on 2008-08-10
Just do "sudo gedit /etc/X11/xorg.conf" that should work for you.

Regards

---

### Post by xodus1 on 2008-08-10
in terminal:

sudo gedit /etc/X11/xorg.conf

enter password when prompted

---

### Post by Kusho on 2008-08-10
Okay how am I supposed to Apply this change??  

I tried the windows tried and true method of getting changes to take effect...  (System, Quit, Restart)

But booted into a "Your system is in low graphics settings.  picked TDFX from the driver pop down, and now back in the normal ubuntu but back to only 800/600, 640/480 or 320/256 as resolution options.

---

### Post by 1337 on 2008-08-10
Maybe try to change Driver to "vesa" instead of "tdfx" in xorg.conf, if from some reason that driver not working. If you will have still problems you can attach here on forums your xorg.conf.

Regards

---

### Post by Kusho on 2008-08-10
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver		"tdfx"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection


EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by Kusho on 2008-08-10
not sure how to do that code window.  sorry.  and I am soo close I know it.  Reput in your part into the screen section, and it loaded.  But think issue is now the Monitor section...  trying to find what the monitor section should be set to.  I'm using a Gateway EV700 1280/1024 max resolution.

---

### Post by 1337 on 2008-08-10
Delete this line [COLOR="Red"]modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync[/COLOR] and restart X (don't add "vesa" as driver yet). You don't need to reboot your system to restart Xsession, after doing changes just push ctrl+alt+backspace and login.

Regards

---

### Post by Kusho on 2008-08-10
That didn't work either.  Atleast can't change the resolution above 800/600 afterwords...

What's the correct way to post code on this site.  spent 5 minutes earlier searching for nothing more than that.  sure there a simple list of ubuntu forum's commands but can't seem to find those either.

---

anyway that section is now...
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
	Gamma	1.0
EndSection

---

### Post by 1337 on 2008-08-10
Try adding this:

```
[COLOR="Red"]in[/COLOR] Section "Monitor"
       Identifier "Configured Monitor"
       Vendorname "Plug 'n' Play"
       Modelname "Plug 'n' Play"	
	[COLOR="green"]Horizsync 30.0 - 70.0
	VertRefresh 50.0 - 110.0
	Option "dpms"[/COLOR]

```

If it still not work for you.

---

### Post by Kusho on 2008-08-10
Yea!!  The elusive 1024/768.

That did it.

---

### Post by Kusho on 2008-08-11
okay that was with me on the way out the door.  on further playing I'm noticing that now windows are fuzzy... think this is due to the refresh rates set up for my monitor...  going to play with that last setting a little...  and can't do any of the visual affects.  curious if that is possible with my video card or might just be a limitation of my processor.

anyway thanks for the help.  if you have any further suggestions on setup please post.  thanks.  will post final settings if i ever get the fuzziness figured out.  it almost like you can see the lines drawing...  so think this is due to the refresh rate on the monitor.  Guessing that issue is that because Ubuntu doesn't recognize my video card, it also can't recognize the type of monitor hooked up to it...  or something like that.

---

### Post by Kusho on 2008-08-11
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Driver "tdfx"
	Screen 0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic CRT Display"
	Modelname	"Monitor 1280x1024"
	Horizsync	31.5-81.0
	Vertrefresh	50-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

### Post by Kusho on 2008-08-11
I think this is the monitor settings i need, and put the settings back for the video card I think, but back to just 800/600 as max resolution...  what am i missing???

---

### Post by 1337 on 2008-08-11
Dont use modeline setting if you are not sure what you are doing get back to the config that worked with horizontal/vertical frenquency I have posted, but in this case don't use option "dpms" set it to off like this:

```

in Section "Monitor"
       Identifier "Configured Monitor"
       Vendorname "Plug 'n' Play"
       Modelname "Plug 'n' Play"    
       Horizsync 31.0 - 69.0
       VertRefresh 50.0 - 160.0
       [COLOR="green"]Option "dpms" "false"[/COLOR]
```

change horizontal and vertical sync also I changed those a bit to match your monitor settings from [here]("http://support.gateway.com/s/MONITOR/7003421/700342102.shtml").


and then set your resolutions like this:

```

...
SubSection "Display"
Depth 24
Modes "1024x768_86" "800x600_86" "640x480_86"
```

(or 76 if that's refresh rate you used)

---

### Post by Kusho on 2008-08-11
Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"
Horizsync 30.0 - 70.0
VertRefresh 50.0 - 160.0
Option "dpms"
EndSection


---
Went back to scratch, and this did it, with changing the frequency up to 75 in system/screen resolution.  think it was just that i had the freq set too low.  Anyway all good.  done playing with this.  Thanks for the help.  Had messed with the wrong thing and the low res setup had screwed it all up, so had to go thru this and piece everything back together.

---

### Post by 1337 on 2008-08-11
I'm glad it worked :)

---

### Post by Kusho on 2008-08-11
fgl_glxgears

tom@tom-ubuntu:~$ fgl_glxgears
No protocol specified
Error: couldn't open display (null)


Does this mean I don't have 3d acceleration?

---

### Post by 1337 on 2008-08-11
Why you use "fgl_glxgears" instead of "glxgears" itself ? try glxgears. Make sure you have installed libglide2 and libglide3 via apt-get/synaptic this may require ldconfig or reboot. Also make sure that you have in xorg.conf: 

```
Load "glx" 
```

And to check if you have 3d acceleration do:

```
glxinfo |grep direct
```

It should give you the text: **direct rendering: Yes** as a positive. If you haven't got those commands install mesa-utils. Fgl_glxgears is for ATI cards :D don't use it on 3dfx card.

Regards

---

### Post by Kusho on 2008-08-11
tom@tom-ubuntu:~$ glxgears
2618 frames in 5.0 seconds = 521.883 FPS
2700 frames in 5.0 seconds = 539.506 FPS
2740 frames in 5.0 seconds = 544.638 FPS

---

### Post by Kusho on 2008-08-11
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

---

### Post by Kusho on 2008-08-11
tom@tom-ubuntu:~$ LIBGL_DEBUG=verbose fglrxinfo
libGL: XF86DRIGetClientDriverName: 1.3.0 tdfx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/tdfx_dri.so
libGL error: dlopen /usr/lib/dri/tdfx_dri.so failed (/usr/lib/dri/tdfx_dri.so: undefined symbol: _glapi_Dispatch)
libGL error: unable to load driver: tdfx_dri.so
display: :0.0  screen: 0
OpenGL vendor string: VA Linux Systems, Inc.
OpenGL renderer string: Mesa DRI Voodoo4 20061113 x86/MMX/SSE
OpenGL version string: 1.2 Mesa 7.0.3-rc2

Segmentation fault

---

### Post by 1337 on 2008-08-11
Hmm, I got an idea... install xserver-xorg-video-tdfx then make sure you have also:

> 	Load		"dri"

in Modules section

and 

> Section "DRI"
	Mode	0666
EndSection

on the end of file. Then reboot. I hope it works. And again not fglrxinfo just glxinfo.

---

### Post by Kusho on 2008-08-11
Done and same thing.

---

### Post by Kusho on 2008-08-11
Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
EndSection
Section "Module"
Load "glx"
Load "dri" 
Load "GLcore"
Load "v4l"
EndSection
Section "ServerFlags"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by Kusho on 2008-10-31
Okay.  8.10 is out and I had to redo this completely.  Now I might be the only one on the planet still using this great video card...  but if theres a second, (as I had to piece thru all of this to find the fix again... 

Here`s what you do.

in terminal:

sudo gedit /etc/X11/xorg.conf

enter password when prompted

Now highlight EVERYTHING and copy this over it.

(I still don`t know the command to show code, so it will be below.  After that, click save, and hit CTRL-ALT-BACKSPACE and should be all good.
----------------------------------------------
# xorg.conf (X.Org X Window System server configuration file)
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
Identifier "Configured Video Device"
Boardname "vesa"
Busid "PCI:1:0:0"
Driver "tdfx"
Screen 0
EndSection

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Plug 'n' Play"
Modelname "Plug 'n' Play"	
Horizsync 30.0 - 70.0
VertRefresh 50.0 - 110.0
Option "dpms"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
Defaultdepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
EndSubSection


EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen 0 "Default Screen" 0 0
EndSection
Section "Module"
Load "glx"
Load "GLcore"
Load "v4l"
EndSection
Section "ServerFlags"
EndSection
------------

---

### Post by Kusho on 2008-11-16
[http://ubuntuforums.org/showthread.php?t=35067](http://ubuntuforums.org/showthread.php?t=35067)

[https://launchpad.net/ubuntu/+source/glide/2002.04.10-16ubuntu2](https://launchpad.net/ubuntu/+source/glide/2002.04.10-16ubuntu2)

[http://www.x-3dfx.com/forum/viewtopic.php?p=2548](http://www.x-3dfx.com/forum/viewtopic.php?p=2548)

Found more of an answer for this...

I just needed to...

now you can choice after restart your system/ or X-Server your resolution.
for 3D support just install " libglide3 " library and ReLink your library like that
" ldconfig " 

Just wish I could get Ubuntu Special Effects working...  What are the requirements for that?

Anyway all normal stuff is running...

---

