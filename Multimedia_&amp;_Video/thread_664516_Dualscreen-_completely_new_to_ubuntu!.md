---
title: "Dualscreen- completely new to ubuntu!"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by cyberphoobz on 2008-01-11
hey there! im completely confused! i dont have a clue what everyone is talking about in the forums! i just want something that i can download and my dualscreen works! or some kind of a walkthru that i can follow and get my dualscreen to work! please somebody help! thank you!

---

### Post by chewearn on 2008-01-11
Two quick questions, so we know how to help you:

1. What is your hardware spec?  Especially graphics cards and monitors, since you are concern about dual screen.

2. Which flavour of ubuntu have you installed: ubuntu, kubuntu, xubuntu, etc?  32-bit (i386) or 64-bit (amd64)?

---

### Post by cyberphoobz on 2008-01-16
well, i got ubuntu, which i just got, i got an ati 9200 graphics card and a compaq mv740 screen and a chimei 938d lcd screen. id like to set up dualscreen with both running on one graphics card. currently im not sure if the name of the chimei is right and if i should use that as the name when editing the xorg file... which i dont know how to do either cos it tells me i hav to be root to edit it. uhm... and the compaq is the main screen at the moment and id liek it to be the secondary one. thats about it i think! at the moment both are clones... so they both do exactly the same! and i got 32 bit.

---

### Post by cyberphoobz on 2008-01-20
Bump!

---

### Post by Jelmoh on 2008-01-20
[HowTo:  Dual Monitors](http://ubuntuforums.org/showthread.php?t=221174&highlight=howto+dual+view).
Here is a walk through that could help you...
Although I'm not sure. Be sure you backup the files you are editing! :)
And, for editing a text file which you need admin rights for:
in terminal:
sudo vim %path to textfile and textfile%

Where sudo gives you admin rights
and vim is a text editor tool in terminal
it's not quite easy to understand, I'll see if I can find a little tutorial! :)

---

### Post by cyberphoobz on 2008-01-20
yes... ive been trying that walkthrough for the last 4 hours... with no results but my xorg stuffing up and me having to put it back to default all the time... pls help! also i do not have the ati driver! i tried installing it... but it didnt work! pls help! thanks for your reply tho! i appreciate it alot!

---

### Post by Jelmoh on 2008-01-20
Quite a lengthy one, but every option in Vim gets explained.. :)
[Vim tutorial](http://www.biochem.ucl.ac.uk/~mckenzie/vim/tutorial.html)

Vim alongside sudo is very powerful, it lets you edit everything without question, by this you can screw up your Ubuntu installation big time!
Always make a backup! (you can read how to in my previous link)

I hope this helps you a bit.. :)
And sorry for my English, sometimes I just can't come up with the words that I mean.. :P
I'm Dutch; that should explain a lot! :P

---

### Post by Jelmoh on 2008-01-20
Also, [this](http://linux.about.com/od/commands/l/blcmdl1_cp.htm) should explain a little bit about the CP command, used to backup files.. :)

---

### Post by cyberphoobz on 2008-01-20
ahm... what has vim got to do with my situation? i am trying to get dualscreen to run! i got an ati 9200 pro graphics card and a chimei cmv938d screen and a compaq Mv740 screen. the first one is with the white cable and the other one is with the blue one... i cant remember what theyre called.. vga or something! and yeah! both work as clones... and in my xorg it sees the compaq as the primary screen... which i dont want it to! thats my problem! also i cant get my dualscreen running!

---

### Post by nanog on 2008-01-20
jelmoh: i do not think you should be recommending vim to new users. 

an easier terminal based alternative is nano. 
sudo nano {path/file}

even easier still is:

sudo gedit {path/file}

---

### Post by cyberphoobz on 2008-01-20
ive been using gedit... thanks! but thats not what i need... i need to know how i need to edit my xorg.conf file to get dual screen running! and the driver for my ati card... and all that stuff!

---

### Post by Jelmoh on 2008-01-20
You tried envy already?
It's a tool to download and install the right driver for you graphics card... :)
I don't know how to act from there unfortunately...
I've got a Nvidia graphics card and that works easily by typing:
nvidia-settings in the terminal, but that doesn't help you obviously

Sorry for the vim part... Vim is a text editor, you need it for editing that conf file.. :)
But as nanog said you'd better use another text editor.. :)

Sorry for not being able to help you completely..!

---

### Post by cyberphoobz on 2008-01-20
i have
ATI radeon 9200 Pro graphics card
First screen: Chimei CMV 938D
Second screen Compaqu MV740!

i tried the sudo aticonfig --query-monitors line but all it said was that tthere was none connected and none enabled. i cant seem to get it to work!

Someone help please

---

### Post by chewearn on 2008-01-21
hi cyberphoobz
Like I said in my PM reply to you, I am unfamiliar with ati; only been using nvidia all the while.

But since your thread is not attracting people who know the answers, I will try to aid in any way I could.

First, could you post your xorg.conf; the one you have working right now?

---

### Post by cyberphoobz on 2008-01-21
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
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"CHIMEI CMV938D"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200 PRO]"
	Monitor		"CHIMEI CMV938D"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768" "800x600" "720x400" "640x480"
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






thats that.... thanks for the help man!

---

### Post by cyberphoobz on 2008-01-21
THANK YOU EVERYONE FOR HELPING! I REALLY APPRECIATE IT! i i ever know anything about computers ill help out in the forums too.. thats one day... when ive learned all this stuff!

---

### Post by chewearn on 2008-01-22
Ok, try the xorg.conf below.

[INDENT]> 
Section "Files"
    FontPath "/usr/share/fonts/X11/misc"
    FontPath "/usr/share/fonts/X11/cyrillic"
    FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath "/usr/share/fonts/X11/Type1"
    FontPath "/usr/share/fonts/X11/100dpi"
    FontPath "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load "i2c"
    Load "bitmap"
    Load "ddc"
    Load "dri"
    Load "extmod"
    Load "freetype"
    Load "glx"
    Load "int10"
    Load "vbe"
EndSection

Section "InputDevice"
    Identifier "Generic Keyboard"
    Driver "kbd"
    Option "CoreKeyboard"
    Option "XkbRules" "xorg"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ImPS/2"
    Option "ZAxisMapping" "4 5"
    Option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "stylus"
    Option "Device" "/dev/input/wacom"
    Option "Type" "stylus"
    Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "eraser"
    Option "Device" "/dev/input/wacom"
    Option "Type" "eraser"
    Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver "wacom"
    Identifier "cursor"
    Option "Device" "/dev/input/wacom"
    Option "Type" "cursor"
    Option "ForceDevice" "ISDV4" # Tablet PC ONLY
EndSection


Section "Device"
    Identifier "ATI Technologies Inc RV280 [Radeon 9200 PRO] 0"
    Driver "ati"
    BusID "PCI:1:0:0"
EndSection

Section "Device"
    Identifier "ATI Technologies Inc RV280 [Radeon 9200 PRO] 1"
    Driver "ati"
    BusID "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier "CHIMEI CMV938D"
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier "COMPAQ MV740"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "ATI Technologies Inc RV280 [Radeon 9200 PRO] 0"
    Monitor "CHIMEI CMV938D"
    DefaultDepth 24

    SubSection "Display"
        Depth 1
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 4
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 8
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 15
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 16
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 24
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "ATI Technologies Inc RV280 [Radeon 9200 PRO] 1"
    Monitor "COMPAQ MV740"
    DefaultDepth 24

    SubSection "Display"
        Depth 1
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 4
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 8
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 15
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 16
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection

    SubSection "Display"
        Depth 24
        Modes "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier "Default Layout"
    Screen "Screen0"
    Screen "Screen1" RightOf "Screen0"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
    InputDevice "stylus" "SendCoreEvents"
    InputDevice "cursor" "SendCoreEvents"
    InputDevice "eraser" "SendCoreEvents"
    Option "Xinerama" "on"
    Option "Clone" "on"
EndSection

Section "DRI"
Mode 0666
EndSection
[/INDENT]


P.S.
I'm working blind, since I don't have ATI (hope I don't mistype anything); if it doesn't work, try to locate the error message; e.g. log-in to console (ALT+F2), type:
[INDENT]```
cat /var/log/Xorg.0.log | grep EE
```
[/INDENT]

---

### Post by cyberphoobz on 2008-01-22
thanks man! yeah ive mucked up the file alot... so i got like... 2000 backup files on my computer! u usally restore em with sudo cp /etc/X11/xorg.conf_backup1888 /etc/X11/xorg.conf!

that just swaps them i think! lol! thanks alot for the help and time ur puttin into me!

---

### Post by cyberphoobz on 2008-01-22
alrite! here we go! good news first... it still started up alright! now the bad news...it didnt activate the dual screen... in fact... it didnt change anything... lol! thats alrite! i appreciate ur help alot! thanks!

---

### Post by cyberphoobz on 2008-01-24
Bump!

---

