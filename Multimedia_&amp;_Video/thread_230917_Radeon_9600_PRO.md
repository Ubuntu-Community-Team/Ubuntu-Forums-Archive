---
title: "Radeon 9600 PRO"
date: 2006-08-06
forum: Multimedia &amp; Video
---

### Post by nightmare03 on 2006-08-06
Hey,

I have a radeon 9600 pro, i've installed fglrx drivers etc..

I have set up compiz but it will randomly lockup before a minute has passed, so i figured it just doesn't like my card and left it.

Now, i've tried to run quake 3 which ran fine when i tried redhat on a old system with a built in graphics adapter a few years ago, now it just freezes when it gets to the menu.

I've ran a gears animation (something to do with glrx or similar, i cant remember the proper spelling) and the gears appeared for a second and my comp just freezes and gives me a black screen and i have to restart.

I have a feeling its driver related (duh), any help would be highly appreciated.

Sorry if i didn't give enough information (driver versions etc..) im not sure what to post so if you need more information just tell me what to give.

Thanks!

---

### Post by nightmare03 on 2006-08-07
Bump! :D

Any assistance would be nice... It's ruining my ubuntu experience :(

---

### Post by nightmare03 on 2006-08-09
Noone? :(

---

### Post by nightmare03 on 2006-08-10
Bah i give up!

I've tried different methods etc.. I've even tried ubuntu 4.10, 5.10 and 6.06 (i think thats the versions)

I used the ati drivers and some graphics worked, glxgears worked and i got average 1200fps, i even managed to use compiz for a while but now it just kicks me off the session and brings me back to the login screen.

I guess the fglrx drivers just hate my card!

---

### Post by Ziox on 2006-08-10
> **nightmare03 said:**
> Bah i give up!

I've tried different methods etc.. I've even tried ubuntu 4.10, 5.10 and 6.06 (i think thats the versions)

I used the ati drivers and some graphics worked, glxgears worked and i got average 1200fps, i even managed to use compiz for a while but now it just kicks me off the session and brings me back to the login screen.

I guess the fglrx drivers just hate my card!

well...be glad that you can use the fglrx driver. because my card isn't even support by fglrx, meaning that I can't boot w/ fglrx...how sucky is that? :confused:

---

### Post by nightmare03 on 2006-08-10
That sucks!

Maybe i can install it but i get no benefits, the ati driver works better lol.

The fglrx driver just crashes my pc when i use things like visualizations on media players etc..

---

### Post by nightmare03 on 2006-08-11
OK, after trying loads of different ways i think im just gonna give up for now and hope something its updated in the future that fixes it!

Some information:

glxgears works with mesa drivers at about 1200 fps.

I install fglrx flawlessly, no errors, no blank screens etc.. Absolutely perfect installation.

fglrxinfo shows the fglrx drivers are installed and running.

I ran glxgears and it will appear on average for only a few seconds, longest it ran for (i thought it was working) was 15 seconds. :(

And thats about it! Anything using gl or GRAPHICS, even will cause my comp to freeze and i have to restart.

General use of ubuntu (firefox, gaim etc...) works fine mostly, until i use visualizations in media players. :S

I guess i'll stick to mesa drivers for now. Hopefully someone else has similar problems and replies ;)

-NiGhTmArE.

---

### Post by Ziox on 2006-08-11
> **nightmare03 said:**
> OK, after trying loads of different ways i think im just gonna give up for now and hope something its updated in the future that fixes it!

Some information:

glxgears works with mesa drivers at about 1200 fps.

I install fglrx flawlessly, no errors, no blank screens etc.. Absolutely perfect installation.

fglrxinfo shows the fglrx drivers are installed and running.

I ran glxgears and it will appear on average for only a few seconds, longest it ran for (i thought it was working) was 15 seconds. :(

And thats about it! Anything using gl or GRAPHICS, even will cause my comp to freeze and i have to restart.

General use of ubuntu (firefox, gaim etc...) works fine mostly, until i use visualizations in media players. :S

I guess i'll stick to mesa drivers for now. Hopefully someone else has similar problems and replies ;)

-NiGhTmArE.

Soo...glxgears doesn't produce any error b4 hard locking?

EDIT: use this command to show more information about your card:

lspci | grep VGA

and

glxinfo | grep rendering

---

### Post by nightmare03 on 2006-08-12
No error before hard locking, no error in xorg.0.log or anything.

I ran the commands :

lspci | grep VGA
```
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
```

glxinfo | grep rendering
```
direct rendering: Yes
```

\\:D/

EDIT:

I've tried different versions of the driver, i can list them if needed.

I've also tried Ubuntu, 4.10, 5.10 and 6.06 out of curiosity, same problem.

:( If only i would get an error, it would be easier no? ](*,)

---

### Post by nightmare03 on 2006-08-13
Just fresh installed ubuntu and this time i used ati driver 22.5 and glxgears plays fine, maximized, dragged around etc...

Before getting my hopes up i installed Unreal Tournament 2004, launched fine, started a game and my comp froze...

It could have just been UT but im betting its the same problems as before :(

Here is my Xorg.conf file

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
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

EDIT:

Just ran glxgears and my comp crashed instantly.

---

### Post by Ziox on 2006-08-13
> **nightmare03 said:**
> Just fresh installed ubuntu and this time i used ati driver 22.5 and glxgears plays fine, maximized, dragged around etc...

Before getting my hopes up i installed Unreal Tournament 2004, launched fine, started a game and my comp froze...

It could have just been UT but im betting its the same problems as before :(

Here is my Xorg.conf file

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
	Screen      0  "aticonfig Screen 0" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig Screen 0"
	Device     "ATI Graphics Adapter 0"
	Monitor    "aticonfig Monitor 0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection


```

EDIT:

Just ran glxgears and my comp crashed instantly.

I know that Xorg does produce an error log, it is located at /var/log/Xorg.0.log (I think, using Windows right now) However, I'm not sure whether it logs all errors, or just the ones produced from login...

---

### Post by nightmare03 on 2006-08-13
I'll post the contents anyway, can't hurt right? :) 

xorg.0.log

Ah, damn, xorg.0.log is too long to post!

---

### Post by nightmare03 on 2006-08-13
More news!

If i load up Ubuntu, open a terminal and run glxgears it will freeze instantly usually BUT! If i load up Ubuntu, press ctrl+alt+backspace then log back in and run glxgears, it will run fine!

Intresting no? :-k

---

### Post by Ziox on 2006-08-13
> **nightmare03 said:**
> I'll post the contents anyway, can't hurt right? :) 

xorg.0.log

Ah, damn, xorg.0.log is too long to post!

Well...i suggest looking at xorg.0.log (make an attachment if it is too long) before and after ctrl+atl+backspace...there must be a difference with, say the different modules that X loads...:-k

---

### Post by nightmare03 on 2006-08-13
I'll do that right now Ziox, stick around :)

---

### Post by nightmare03 on 2006-08-13
I've attached the xorg.0.log (renamed to txt) files in zip archives, they are too big to upload :-k 

Startup = Xorg.0.log from when i first login
Restart = xorg.0.log from when i do ctrl+alt+backspace and login

There is hundreds of lines like below in both xorg files, i mean LOADS :

```
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

:-k

---

### Post by Ziox on 2006-08-13
> **nightmare03 said:**
> I've attached the xorg.0.log (renamed to txt) files in zip archives, they are too big to upload :-k 

Startup = Xorg.0.log from when i first login
Restart = xorg.0.log from when i do ctrl+alt+backspace and login

There is hundreds of lines like below in both xorg files, i mean LOADS :

```
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

:-k

Man I love dual screen !!! :D  Ok anyhoo...here's the first section that's different:

Start: 

```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
```

Restart:

```
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
```

I don't know if it makes a difference or not, but I'll keep on looking.  I'm posting just so that it is faster w/ updates...(if that makes sense)

---

### Post by Ziox on 2006-08-13
here's the last part that is different from what I can see:

Restart:
AUDIT: Sun Aug 13 17:49:30 2006: 5355 X: client 2 rejected from local host

Startup:
[Nothing]

So...I have no idea what to do, but hopefully this can help someone who has the knowledge to solve this...

EDIT: both parts are at the end of the file...

---

### Post by nightmare03 on 2006-08-13
Yeah i hope so too!

Thanks for posting them differences Ziox.

---

### Post by nightmare03 on 2006-08-13
*bump* :D

---

### Post by nightmare03 on 2006-08-15
My last bump :(

---

### Post by Pettman on 2006-08-15
I've also got a problem with the fglrx drivers and a radeon 9600 pro causing the system to freeze, I've searsched all over the internet and so far I've found nothing :(. It has been around at least since Breezy, one thing I've noticed is that CPU usage goes up to maximum before the crash. Personly I suspect that there is something wrong with the drivers ATi provides.

---

### Post by mrchaotica on 2006-08-15
> **nightmare03 said:**
> More news!

If i load up Ubuntu, open a terminal and run glxgears it will freeze instantly usually BUT! If i load up Ubuntu, press ctrl+alt+backspace then log back in and run glxgears, it will run fine!

Intresting no? :-k

Actually, this really **is** interesting, because I've got a similar symptom with my (seemingly completely different) problem! Read my thread [here]("http://www.ubuntuforums.org/showthread.php?p=1384134").

My graphics issue is that it the first time X runs, it displays at 640x480 (which is wrong), but after I kill it with ctrl-alt-backspace it displays at 1280x1024 (which is correct). The funny thing is, I've got a completely different card than you (nVidia instead of ATI), and the problem isn't with the card anyway.

The commonality between us is that *both* our problems are caused by X failing to recognize a piece of hardware the first time (in your case the graphics card, in mine the monitor) but succeeding the second time. In other words, it might be a bug in X itself, and there could be hope for your Radeon working correctly yet!

Oh and thanks, by the way -- reading your thread gave me the clue to look at the Xorg log to figure out what my issue was.

---

### Post by cyberface on 2006-08-16
Hi,

I'm fighting with my ATI Card and desktop freezes, too.

with the mesa driver my desktop froze because of opengl screensavers. 

After switching to the ones from ati my destop freezes after jumping back from konsole with Strg+Alt+F7 and during wakeup from hipernate.

I tried both the driver from the reposories (restricted modules + xorg-driver-fglrx vesrion 7.0.0-8.25.18+2.6.15.11-3) and the new one from ati homepage (8.27.10-1) following this tutorial:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

I'm afraid this is no driver issue as I already ran two different versions of atis own drivers with opensuse on the same machine, without having any similar problems.
Suse didn't jump to version 7 of x-server so far. Perhaps this problem has something to do with X.

Regards

PS: I'm using a RADEON 9600 TX

---

### Post by Ziox on 2006-08-16
have you guys checked for bug reports? If there isn't any, then it is time to file one...

---

### Post by ex00r on 2006-08-16
I also get randomly freezes if i run XGL. I also have a Radeon 9600XT and the fglrx drivers from the repos.

I found no solution yet, but know others who have also freezes with radeon 9600 + XGL

so i think its driver related.

at least sometimes my machine is running for 2-3 hours before all freezes and i have to hard reboot.

glxgear is crashing with XGL, with X its just fine and haven't tried these CTRL+ALT+BACK-thingie

---

### Post by nightmare03 on 2006-08-16
Seems to be 9600 related hmm...

---

### Post by Ziox on 2006-08-16
Just wondering, does anyone of you know if this problem occurs in previous Xorg? I think there are some regressions in Xorg, and if that's the reason, then it should be reported, and be fixed for the next release...

---

### Post by nightmare03 on 2006-08-17
I've used older versions of ubuntu and i assume they came with older xorg versions?

The problem still occured :(

---

### Post by Pettman on 2006-08-17
> **Ziox said:**
> Just wondering, does anyone of you know if this problem occurs in previous Xorg? I think there are some regressions in Xorg, and if that's the reason, then it should be reported, and be fixed for the next release...I had exactly the same error in 5.10.> **Ziox said:**
> have you guys checked for bug reports? If there isn't any, then it is time to file one...
Where? EDIT, found the place.. searsching for fglrx freeze gives 19 results.[See here]("https://launchpad.net/distros/ubuntu/+bugs?field.searchtext=fglrx+freeze&orderby=-importance&search=Search&field.status%3Alist=Unconfirmed&field.status%3Alist=Confirmed&field.status%3Alist=In+Progress&field.status%3Alist=Needs+Info&field.status%3Alist=Fix+Committed&field.assignee=&field.owner=&field.omit_dupes=on&field.has_patch=&field.has_no_package=")

---

### Post by cyberface on 2006-08-18
Okay guys, I spent some time on reading bugreports and finally I found a solution.

Our problem is related to the fglrx driver.

after adding this line
```
Option "AGPv3Mask" "0x00000002"
```

in the device section of xorg.conf

which disables agp 8x.

I can switch to console and back to the x-server.

I didn't test my hibernate freeze problem so far, but as much as I read this is related to antother bug.

After some tests I will tell you more

Regards

---

### Post by nightmare03 on 2006-08-18
Wow nice!

Try running glxgears from a first boot up and report back please. :)

---

### Post by cyberface on 2006-08-18
I never had any problems running glxgears

and I already ran fgl_glxgears, which worked fine: 400-500fps

Regards

---

### Post by nightmare03 on 2006-08-18
cyberface, thanks so much!!!

Adding that line makes everything work now! (So far anyway), compiz is working flawless as is everything else.

Really really reallllly appreciate it cyberface!!

---

### Post by Pettman on 2006-08-18
nightmare03, what chipset do you have?

---

### Post by nightmare03 on 2006-08-20
What do you mean? Im not sure how to check...

The brand on the box was Connect3D

---

### Post by Pettman on 2006-08-20
> **cyberface said:**
> Our problem is related to the fglrx driver.

after adding this line
```
Option "AGPv3Mask" "0x00000002"
```

in the device section of xorg.conf

which disables agp 8x.

Seems to be workin for me :), victory at last (after more than a year of struggle)!

> **nightmare03 said:**
> What do you mean? Im not sure how to check...

The brand on the box was Connect3D

I've got a VIA KT600 northbridge and a VT8237 southbridge chipset, they control a lot of things including the AGP buss. Easiest way to check is probably to know what motherboard you've got and then look it up in the specifications.

---

### Post by nightmare03 on 2006-08-21
My chipset is :

VIA KT400(A)
VIA VT8235

:D 

That fix is fantastic :cool: One line of text fixes everything.

---

### Post by Pettman on 2006-08-22
> **nightmare03 said:**
> My chipset is :

VIA KT400(A)
VIA VT8235Hmm... seems like the via chip-sets dont get along wiht the ATi dirvers when running AGP x8 :(

---

### Post by nightmare03 on 2006-08-22
Oh well, its not really a big deal now we have a fix :D

---

### Post by dazedx on 2006-09-01
Hot diggity damn !! .. 

I've been looking for a solution to this for a while. I'm going to try it the moment i get home from work !!

---

### Post by ex00r on 2006-09-03
but how do we spread the message?

by the way, i also have a VIA chip...

---

