---
title: "Dual Monitor, Separate X Sessions Question?"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by BassKozz on 2008-02-19
After [alot of xorg.conf work]("http://ubuntuforums.org/showthread.php?t=699762"), I now have my Dual Monitor Display setup.
I have a couple of questions:
[list=1]
[*]Each monitor is a separate X Session.  My question is, is it possible to transfer a running program/window from one X session to another?
_For Example_: if I open up FireFox on Monitor #1, how can I transfer it to Monitor #2? (w/out closing and re-opening)
Is this possible?

[*]The Xsession on one of my monitors doesn't have title bars on the windows:
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_notitlebars.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/notitlebars.jpg)
*(Click to see larger)*
So there is no where to grab onto and move, minimize, maximize, close (X) :confused:[/list]
Here is what my other (working) X Session looks like, notice it does have the Title Bars on the windows:
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_wtitlebars.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/wtitlebars.jpg)

---

### Post by BassKozz on 2008-02-19
:bump: :(

---

### Post by ArchangHell on 2008-02-19
1- I'm also interested in your first question.

2- Have you the confizconfig? In the desktop without title bars, run it and be sure that in "effects" you have "windows decoration" activated.

Hope it works, and someone answers the first question.

---

### Post by BassKozz on 2008-02-19
> **ArchangHell said:**
> 2- Have you the confizconfig? In the desktop without title bars, run it and be sure that in "effects" you have "windows decoration" activated.

Yah, I've looked thru all the CompizConfig Settings and they all seem to be fine... the other odd thing to note about this is that no matter where I open CompizConfig (on screen #1 or screen #2) the changes that I make affect the other screen (and vice versa), so it doesn't make sense that one screen has window title bars, and the other doesn't :confused:

---

### Post by ArchangHell on 2008-02-19
So if you disable conpiz everything works fine? Just to catch the problem.

---

### Post by BassKozz on 2008-02-19
> **ArchangHell said:**
> So if you disable conpiz everything works fine? Just to catch the problem.
Yup, wouldn't you know it, Compiz Disabled restores window title bars... geez, why didn't I think of trying that ](*,)
I went to System->Preferences->Appearance and change the *Visual Effects* to **NONE**, the problem goes away, meaning Window Title Bar's show up in both Display's...
I then went back and changed *Visual Effects* to **Normal** and it's still works, :D it's fixed ... (for now) [-o<
So this confirms it's a Compiz issue, now to find out what/why it's behaving this way :confused:
Thanks ArchangHell

Anyone want to take a crack at **Question #1**?

---

### Post by BassKozz on 2008-02-19
> **ArchangHell said:**
> 1- I'm also interested in your first question.
It doesn't look good my friend:
[quote="[http://en.wikipedia.org/wiki/Xinerama](http://en.wikipedia.org/wiki/Xinerama)"]
Unfortunately, the independence of each screen (which you get when not using Xinerama) has a noteworthy usability problem: **There is no way to move windows between the different screens**. A few applications and libraries provide an equivalent behaviour: they can remove their own windows from one screen, and recreate them on the other screen. However, only a few applications can do this, and it's usually difficult to use.[/quote]
So unless we go w/ Xinerama (which would remove the dual X Sessions and create one big/long screen) it doesn't look like we can move programs from screen to screen...
Hopefully someone more knowledgeable on the subject will chime in, but as it looks, it can't be done :(

---

### Post by BassKozz on 2008-02-20
> **B/-\ssKozz said:**
> Yup, wouldn't you know it, Compiz Disabled restores window title bars... geez, why didn't I think of trying that ](*,)
I went to System->Preferences->Appearance and change the *Visual Effects* to **NONE**, the problem goes away, meaning Window Title Bar's show up in both Display's...
I then went back and changed *Visual Effects* to **Normal** and it's still works, :D it's fixed ... (for now) [-o<
So this confirms it's a Compiz issue, now to find out what/why it's behaving this way :confused:
**_UPDATE:_**
I rebooted my machine last night, and it went back to it's old ways (no window title bars on the secondary monitor/display):(
So I turned Compiz Off and Back on again and the system froze :(
I then rebooted, and this time the reverse happened;
My main monitor (primary display) was missing Window Title Bars and the secondary monitor/display had them :confused:

***So for now, I am leaving Compiz off until I can get an answer to why this is happening, and how to fix?***
:anyone, anyone, Bueller, Bueller: ):P

---

### Post by ArchangHell on 2008-02-20
Well I've tried in a clean installation with only the restricted drivers activated, and no title bars in windows of the second desktop. Compiz deactivated... title bars are back.
So it seams that is really a compiz problem, and not your configuration.

 Let's keep on waiting for a more proactive intervention.

---

### Post by BassKozz on 2008-02-20
> **ArchangHell said:**
> Well I've tried in a clean installation with only the restricted drivers activated, and no title bars in windows of the second desktop. Compiz deactivated... title bars are back.
So it seams that is really a compiz problem, and not your configuration.

 Let's keep on waiting for a more proactive intervention.
Thanks for the update, I was beginning to think Envy was the source of my problems, so it's good to know that even with *restricted drivers* this issue remains.
...
BTW, Referring to Question #1 adamk over at the compiz-fusion forums reported that:
[quote="[http://forum.compiz-fusion.org/showpost.php?p=49672&postcount=4](http://forum.compiz-fusion.org/showpost.php?p=49672&postcount=4)"]Correct, it can't be done without xinerama or twinview. And you are much better off using twinview than xinerama, as their are issues when using the xinerama and composite extensions at the same time.[/quote]:(
That's a bummer, oh well guess you can't have your cake and eat it too:p

---

### Post by BassKozz on 2008-02-23
:BUMP:
Can someone help ArchangHell and me with ***Question #2***:
> **B/-\ssKozz said:**
> After [alot of xorg.conf work]("http://ubuntuforums.org/showthread.php?t=699762"), I now have my Dual Monitor Display setup.
...
[list]
[*]The Xsession on one of my monitors doesn't have title bars on the windows:
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_notitlebars.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/notitlebars.jpg)
*(Click to see larger)*
So there is no where to grab onto and move, minimize, maximize, close (X)[/list]
Here is what my other (working) X Session looks like, notice it does have the Title Bars on the windows:
[[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/th_wtitlebars.jpg[/IMG]](http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/wtitlebars.jpg)
> **B/-\ssKozz said:**
> Yup, wouldn't you know it, Compiz Disabled restores window title bars... geez, why didn't I think of trying that ](*,)
I went to System->Preferences->Appearance and change the *Visual Effects* to **NONE**, the problem goes away, meaning Window Title Bar's show up in both Display's...
I then went back and changed *Visual Effects* to **Normal** and it's still works, it's fixed ... (for now) [-o<
So this confirms it's a Compiz issue, now to find out what/why it's behaving this way?
Thanks ArchangHell
> **B/-\ssKozz said:**
> **_UPDATE:_**
I rebooted my machine last night, and it went back to it's old ways (no window title bars on the secondary monitor/display):(
So I turned Compiz Off and Back on again and the system froze :(
I then rebooted, and this time the reverse happened;
My main monitor (primary display) was missing Window Title Bars and the secondary monitor/display had them :confused:

***So for now, I am leaving Compiz off until I can get an answer to why this is happening, and how to fix?***

---

### Post by fwre01 on 2008-02-23
B/-\ssKozz, i am trying to set up seperate X sessions on my two monitors, but havent been able to get it going. could you post your Xorg config file (or the relevant parts) so i can look through it? are you running your monitors on seperate cards?

---

### Post by BassKozz on 2008-02-23
> **fwre01 said:**
> B/-\ssKozz, i am trying to set up seperate X sessions on my two monitors, but havent been able to get it going. could you post your Xorg config file (or the relevant parts) so i can look through it? are you running your monitors on seperate cards?

I am using only 1 card, [MSI NX8600GT-T2D256EZ]("http://www.msicomputer.com/product/p_spec.asp?model=NX8600GTS-T2D256EZ-HD&class=vga") (as listed in sig) she's not the fastest board on the block but I figure she should be able to handle compiz on 2 monitors (am I wrong???)...
Here is my xorg.conf file:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:26:48 PST 2008

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Fri Jan 11 14:27:25 PST 2008
# xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "Screen0" 0 0
  screen 1 "Screen1" rightof "Screen0"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "ServerFlags"
	Option		"Xinerama"	"0"
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
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Horizsync	30.0	-	65.0
	Vertrefresh	50.0	-	75.0
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"Monitor0"
	Vendorname	"Unknown"
	Modelname	"HSD HG216"
	Horizsync	30.0	-	82.0
	Vertrefresh	50.0	-	75.0
EndSection

Section "Monitor"
	Identifier	"Monitor1"
	Horizsync	28.0	-	64.0
	Vertrefresh	43.0	-	60.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600 GT]"
	Driver		"nvidia"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 8600 GT"
	Option		"AddARGBGLXVisuals"	"True"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection

Section "Device"
	Identifier	"Videocard1"
	Driver		"nvidia"
	Vendorname	"NVIDIA Corporation"
	Boardname	"GeForce 8600 GT"
	Option		"AddARGBGLXVisuals"	"True"
	Busid		"PCI:1:0:0"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G80 [GeForce 8600 GT]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Modes		"1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"DFP: 1680x1050 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"DFP: 1280x1024 +0+0"
	Option		"AddARGBGLXVisuals"	"True"
	SubSection "Display"
		Depth	24
		Modes		"nvidia-auto-select"
	EndSubSection
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by BassKozz on 2008-03-04
Can someone please help me with this :roll:

---

### Post by jakornblum on 2008-03-31
:bump:
I am having both of these problems.. disabling compiz (or dumbing it down) is not really a viable option here.  I would really like the titlebars on my second display.

If you are stuck on this (like me) an easy way to move windows around with no title bar is by holding alt and clicking with the mouse to move the windows.

Any ideas on how to solve these problems?

---

### Post by Prefix100 on 2008-03-31
Run the following command on the x that doesn't have title bars.

```
compiz --replace
```

If that works add it to sessions ( System > Preferences > Sessions ),

hope that fixes problem two.

---

