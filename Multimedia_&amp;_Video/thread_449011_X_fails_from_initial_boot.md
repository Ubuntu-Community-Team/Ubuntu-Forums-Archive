---
title: "X fails from initial boot"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by TerrorAndHubris on 2007-05-19
Hello all. May I start out by saying ATi+Linux sucks nuts. This is the latest episode of my troubles with ATi and X, this time being more frustrating than ever.

So basically what I've done is, using the Alternate install cd so that I could use Windows' bootloader rather than GRUB, I installed a fresh copy of Feisty. After twerking with making sure everything boots properly, I went ahead to fire up Ubuntu for the first time, only to be discouraged by X crashing right after the loading bar completed.

Where I think I may have gone wrong was in specifying my monitors supported resolutions. At the part of the installation process where it asks what resolutions should be supported, I selected as many as I know are supported by my monitor, starting with 1680x1050.

Anyhow, the keywords at the end of the X printout of what happened was something along the lines of no screens supported, and right before it it says screen(s) detected but not supported, or something to that effect.

Any help to someone having a b*tch of a time with linux?

---

### Post by Herman on 2007-05-19
Hello TerrorAndHubris,
Try mounting your Ubuntu filesystem in the Live CD and editing your /etc/X11/xorg.conf file.
Here are two other threads you should look at where the same (or similar) subject, [LCD Monitor Out Of Range Problem]("http://ubuntuforums.org/showthread.php?t=447483")       [FGLRX - ati x1650 - am I wasting my time?]("http://ubuntuforums.org/showthread.php?t=447510")
Those should help you. It's not difficult at all when you know what to do. I love my ATI card and my new 20"W monitor with 1650x1050 resolution in Feisty!
Regards, Herman :)

---

### Post by TerrorAndHubris on 2007-05-19
Hey, thats a pretty good idea, but one question: what is it that I should edit? I took a peek at xorg.conf while running in text mode and everything *looks* ok.

---

### Post by Herman on 2007-05-19
Well for me it was those lines with all the resolutions listed in them for each different depth in the display, as illustrated in those links, especially that first link. :)  Did you click on the links I posted? (You're supposed to read those links). :)  Maybe they aren't clear enough. ...Okay, I'm editing that first link right now and making the changes red and bold to make sure they stand out.

Does that look like it might be your problem, or is your problem something a little different?
In that second thread glenndavy was asking if I was using the fgrlx driver and I tried it a couple of times following different how-tos but neither would work for me, I had to keep restoring the xorg.cof with the ati driver from backup .  
You may need to run 'sudo dpkg-reconfigure xserver-xorg' and see if that helps. What video card do you have anyway? Mine's an ATI Radeon 9200.
Here's a link I made a while back on running 'sudo dpkg-reconfigure xserver-xorg' in case it helps you,  [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html"). It's easy to run 'sudo dpkg-reconfigure xserver-xorg' if you know what hardware you have. You can also do ' lspci -x | grep -i "vga\|display"' to check up about your PCI bus identifier too if you like. You should do that beforehand if possible.```
 lspci -x | grep -i "vga\|display"
```Regards, Herman :)

---

### Post by TerrorAndHubris on 2007-05-20
I followed that Xserver guide (which perfectly shows what my problem is)  with no success, just new errors that were vague. 

System info:

Dell Inspiron E1505

ATi Mobility Radeon X1400

Dell 2007WFP Monitor
Max/Optimum resolution: 1680x1050 @ 60Hz
Hsync Range: 30 to 81
Vsync Range: 56 to 76

```
knoppix@Knoppix:~$ lspci -x | grep -i "vga\|display"
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
knoppix@Knoppix:~$

```

---

### Post by Herman on 2007-05-20
Hmmm,
Okay then, can you please post your /etc/X11/xorg.conf here and I'll try comparing it to mine and combe through it to see if I can spot anything wrong with it.
If I can't maybe someone else browsing the forums here can help.

Maybe if you have a different monitor lying around or know where you can borrow one you could try plugging that in and see if you can get that one to work. Then try again with the 1680x1050 one later.  
EDIT: Many laptops will have a VGA port at the back for plugging in a separate monitor or a projector for giving presentations. The logic of this is to see if we can get your ati card working to begin with and then work on the monitor half of things later. Sometimes breaking problems down into smaller categories can help.

Does it work with Knoppix? Mine did too! If Knoppix can make it work then surely there is hope. You should at least be able to get it working with the vesa driver for now even if you can't get the ati driver to work. 
Regards, Herman :D

---

### Post by TerrorAndHubris on 2007-05-20
Not sure how well this will help, as this is the reconfigured xorg file that prompted another error. I have a little suspicion that the mouse is causing it; I wasn't sure what to choose; I have a Logitech wireless usb mouse.

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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-81
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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

```

Knoppix works, and so did Edgy.

---

### Post by Herman on 2007-05-20
Okay, thanks for that, I changed the resolutions for you and the name of the monitor. 
I see you are using the vesa driver in this xorg.conf already. That should work. I would like to try out the ati driver but I don't think it's a good idea to complicate things by making too many changes at once. Most of the rest of it looks reasonable to me.

Try editiing your xorg.cong file like this,  (you can copy and paste this one if you want, or parts of it, it's up to you.  It will certainly never work with the resolutions you have there, so it won't do any harm and may fix it. If that gets it working we'll try upgrading to the ati driver next. (And maybe we will anyway).
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
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/cyrillic"
    FontPath    "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/usr/share/fonts/X11/100dpi"
    FontPath    "/usr/share/fonts/X11/75dpi"
    # path to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ExplorerPS/2"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"        "/dev/psaux"
    Option        "Protocol"        "auto-dev"
    Option        "HorizScrollDelta"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "ForceDevice"    "ISDV4"        # Tablet PC ONLY
EndSection

Section "Device"
    Identifier    "Generic Video Card"
    Driver        "vesa"
    BusID        "PCI:1:0:0"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "DELL 2007WFP"
    Option        "DPMS"
    HorizSync    30-81
    VertRefresh    56-76
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Generic Video Card"
    Monitor        "DELL 2007WFP"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1920x1200" "1680x1050" "1280x800" "1152x720" "800x500"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice     "stylus"    "SendCoreEvents"
    InputDevice     "cursor"    "SendCoreEvents"
    InputDevice     "eraser"    "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "DRI"
    Mode    0666
EndSection
``` This is your own xorg.conf file back again but with resolutions that should suit your monitor. Try that in your machine and see if it works! 
Good Luck
Regards, Herman :D

---

### Post by TerrorAndHubris on 2007-05-20
She's still crashing. I wrote down some of the interesting parts of the error messages to see if they would help.

When I go through the *dpkg-reconfigure xserver-xorg*, this is my error:

```
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal Sserver Error:
no screens found
```

Now more interestingly, when I used your edited xorg.conf file I got this:

```
Fatal Server Error:
Caught signal 11. Server Aborting.
```

That was displayed right after a backtracking list that was rather cryptic.

In the more detailed error output I found two interesting lines:

```
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
```

That could really be nothing, especially when I saw about twenty lines that said this, right before the backtracking and fatal server error message:

```
(II) VESA(0): Not using mode "1680x1050" (No mode of this name)
```

Like I said, there were about twenty or so lines like that, each with a different resolution stated in quotes.

Now what do I do, besides selling my soul to Windows?

---

### Post by Herman on 2007-05-21
I picked up a tip you could try, your Live CD works, right?
Look at this suggestion by vikramsharma in post #2 of this thread, [generic video driver?]("http://ubuntuforums.org/showthread.php?t=447530&highlight=xorg.conf")             
Well try running your Ubuntu LiveCD and copying the Live CD's /etc/X11/xorg.conf into your hard disk installed system, like this,
```
sudo mkdir /media/ubuntu
``````
sudo mount -t ext3 /dev/hda2 /media/ubuntu
``````
sudo cp /etc/X11/xorg.conf /media/ubuntu//etc/X11/xorg.conf
```I'm sorry, I was testing that idea out but I ran out of time to fully test it, but I guess it won't hurt to give it a try anyway. I noticed my main computer runs the ati driver when I'm running the Live CD, I was surprised about that. It runs in the resolutions I told you would never work though. Ironically, it was changing the resolutions that fixed it for me in the hard disk installed system in the same computer. 'Go figure', as they say.
So I hope I didn't steer you in the wrong direction back there. I also read that vesa doesn't support those resolutions I gave you, so you could try replacing 'vesa' with 'ati' in that file first, that might fix it.  And comment out the line about '
/usr/share/fonts/X11/cyrillic' for now too, I think. 

Try those ideas and see anything helps,
Regards, Herman :D

EDIT: I just found these two links, they look like they will help you,  [Envy]("http://albertomilone.com/nvidia_scripts1.html")   and         [Installing ATI Drivers on Ubuntu 7.04 guide]("http://ubuntuforums.org/showthread.php?t=438008")

---

