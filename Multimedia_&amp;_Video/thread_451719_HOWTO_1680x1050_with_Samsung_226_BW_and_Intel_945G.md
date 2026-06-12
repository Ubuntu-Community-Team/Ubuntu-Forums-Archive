---
title: "HOWTO: 1680x1050 with Samsung 226 BW and Intel 945GM (i810) on Kubuntu Feisty"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by capdog on 2007-05-22
After about 20 long hours, pouring over log files and trawling Google, I finally managed to get my monitor to display the correct resolution when hooked up to my laptop, Here are the hardware specs:

**LAPTOP**

HP Hewlett Packard NX7300
Intel Core 2 Duo T5600 1.83GHz
Intel Graphics 950
Intel Chipset 945GM Express
Intel Pro Wireless 3945ABG
1 gig RAM
120gig SATA Drive
15.4" Brightview

There is no DVI or S-Video port on the laptop, only the VGA out.

[Click here for the link to HP laptop specs.]("http://h10010.www1.hp.com/wwpc/za/en/sm/WF06b/1781533-1781641-1781641-1781641-12434630-12924030-78094391.html")

**MONITOR**

Samsung SyncMaster 226BW
22"
1680x1050 native resolution

**INTEL ONBOARD GRAPHIC CARD (output from lspci)**

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
```

**OPERATING SYSTEM**

Kubuntu Feisty 7.04
2.6.20-15-generic

**STEPS**

PLEASE NOTE: This is important. On every reboot, while GRUB is starting, push FN-F4 to switch the laptop display off and have only the Samsung monitor on. This can be done before Kubuntu loads, and I think it's important to have only the Samsung on while trying to get the resolution correct.

**CONFIGURING XORG**

The laptop's original xorg.conf looked like this, and was set up at install time:

```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
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
```

That worked fine for the laptop screen's native res of 1280x800. 

To start with, remove the lines:

```
HorizSync	28-64
VertRefresh	43-60
```

from the "Monitor" section, and restart with the Samsung external monitor plugged in (remembering to FN-F4, switching to external display only) in order to allow the "ddc" module of xorg to report what modes the monitor is capable of. This information is then used to make a ModeLine. To do that, wait until your desktop is back up again, look in the file /var/log/Xorg.0.log (the log file for xorg) and find these lines:

```
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 119.0 MHz Image Size: 474 x 296 mm
(II) I810(0): h_active: 1680 h_sync: 1728 h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) I810(0): v_active: 1050 v_sync: 1053 v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) I810(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 140 MHz
```

Use these values to construct the following lines, which are highly specific to the make and model of the monitor:

```
Modeline	"1680x1050" 119.0 1680 1728 1760 1840 1050 1053 1059 1080
DisplaySize	474 296
```

You can see in it how the values correspond to what is found in the log. You can then make up a new xorg.conf, with these lines included, and some other changes (notably the Screen section):

```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	DisplaySize	474 296
	HorizSync	30.0 - 81.0
	VertRefresh	60.0
	Option		"DDC" "FALSE"
	Modeline	"1680x1050" 119.0 1680 1728 1760 1840 1050 1053 1059 1080
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		16
		Modes		"1680x1050" 
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Note: instead of giving the VertRefresh value of "56 - 75" (as reported in the Xorg.0.log above), set it to 60 only. This is critical, as xorg always seems to select the wrong refresh rate when specifying a range!

Note: Turn off DDC module now in the section "Monitor" using "Option "DDC" "FALSE"" I am fairly sure this is necessary, and we are specifying the ModeLine anyway so don't need it.

**915resolution**

Install the 915resolution command line app that allows you to change the video bios (not permenantly). This is needed to trick the i810 driver into displaying a slightly non-standard resolution. To get it, run:

```
sudo aptitude install 915resolution
```

The installation automatically creates a file /etc/default/915resolution, which is a plain text file and is the settings for the "default" video mode that 915resolution should patch on startup. I edited this file and set it to AUTO, simply because it doesn't do quite what it needs to (explained futher down):

```
#
# 915resolution default
#
# find free modes by  /usr/sbin/915resolution -l
# and set it to MODE or set to 'MODE=auto'
#
# With 'auto' detection, the panel-size will be fetched from the VBE
# BIOS if possible and the highest-numbered mode in each bit-depth
# will be overwritten with the detected panel-size.
MODE=AUTO
#
# and set resolutions for the mode.
# e.g. use XRESO=1024 and YRESO=768
XRESO=
YRESO=
#
# We can also set the pixel mode.
# e.g. use BIT=32
# Please note that this is optional,
# you can also leave this value blank.
BIT=
```

The next step is to hack the video BIOS, first, type this:

```
sudo 915resolution -l
```

And you should see:

```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 512x771, 8 bits/pixel
Mode 61 : 512x771, 16 bits/pixel
Mode 62 : 512x771, 32 bits/pixel
Mode 63 : 2208x771, 8 bits/pixel
Mode 64 : 2208x771, 16 bits/pixel
Mode 65 : 2208x771, 32 bits/pixel
```

You then need to hack 3 modes, by executing the following as root/sudo which should give you the changes as reflected beneath:

```
915resolution 3a 1680 1050 8 1840 1080
915resolution 4b 1680 1050 16 1840 1080
915resolution 5a 1680 1050 32 1840 1080
```

Now you get when typing "915resolution -l":

```
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 945GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : **1680x1050, 8 bits/pixel**
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : **1680x1050, 16 bits/pixel**
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : **1680x1050, 32 bits/pixel**
Mode 5c : 1920x1440, 32 bits/pixel
Mode 60 : 512x771, 8 bits/pixel
Mode 61 : 512x771, 16 bits/pixel
Mode 62 : 512x771, 32 bits/pixel
Mode 63 : 2208x771, 8 bits/pixel
Mode 64 : 2208x771, 16 bits/pixel
Mode 65 : 2208x771, 32 bits/pixel
```

Note: It is critical to choose the modes 3a,4b and 5a! These replace the 1600x1200 resolution, and replacing the others simply doesn't work.

Note: It is also important to set the color depths of the three changes to 8, 16 and 32. This is despite the xorg.conf about only having sections for 24 and 16, and having DefaultDepth=24. When I tried to get the monitor working with mode 5a hacked to 24bit, it didn't work, and I suspect this is the one thing that I spent the most time trying to figure out. Especially since the man page of the i810 driver says it doesn't support 32 bit!

Note: The values "1840 1080" at the end of each 915resolution line come from the "h_blank_end" and "v_blanking" values from the log file (where I made the ModeLine above). These are also critical to get it to work.

If you are seeing the line: ```
Not using mode "1680x1050" (no mode of this name) 
``` in your Xorg.0.log file, make sure that you're hacking the correct resolution and using the right bit rates! 

You can add the three lines to your "/etc/init.d/rcS" file in order to have them run at startup.

Right... checklist...

1) xorg.conf file set up
2) the 915resolution hack is in the startup script and ready to be applied at next boot
3) said a little prayer to your diety of choice? ;)

Reboot, push FN-F4 during GRUB to switch to external monitor, and hope for the best!

On my laptop, it boots straight into 1680x1050 paradise! But you may have to go into the KDE System Settings dialog and move the slider over to the "1680x1050" resolution.

The great thing is that with the Samsung unplugged, the same xorg.conf boots the laptop screen into it's native resolution perfectly too. That is enough for me (I have no desire to start messing with clone or spanning dual-display modes!)

**TIPS IF YOU HAVE SLIGHTLY DIFFERENT HARDWARE OR SIMPLY CAN'T GET THIS TO WORK**

- I tried to get the xserver-xorg-video-intel driver (the "newest" one apparently) to work, but had no success with this. It is supposed to negate the need to use the 915resolution hack, but no luck!

- Watch the log "Xorg.0.log" closely! Study it! Everything you need to know about what is going on, is in there. If you don't understand it, try Google for the keywords you need help with. Understanding the log was the key to me finally working out where my attempts were failing.

- Make it easy to investigate the log while constantly restarting X. Do this by placing a shortcut link on your desktop to open the log with one click, instead of having to open a terminal, change dir and open it manually. Also make a script which runs "kdesu kate /etc/X11/xorg.conf", or "gksudo gedit /etc/X11/xorg.conf", to edit the xorg.conf file, and place a shortcut to that on your desktop too. This makes clicking to the frequently accessed files easier and ultimately you can move through attempts quicker.

- Use the built in menu on your monitor itself to check what resolution it is detecting. It normally displays this when you push the menu button on the front. This is also very useful for troubleshooting attempts.

- If it doesn't work on first boot, try restarting the X server with CTRL-ALT-BACKSPACE. This is easier than rebooting the entire PC.

**CREDITS**

This post on the Debian forum, 90% of the information I needed:
[http://forums.debian.net/viewtopic.php?t=14242](http://forums.debian.net/viewtopic.php?t=14242)

The following blog entry contained a few tidbits:
[http://www.wahlau.org/samsung_225bw_with_xorg_on_ubuntu_linux](http://www.wahlau.org/samsung_225bw_with_xorg_on_ubuntu_linux)

I've never been quite as happy as I was the first time I saw native res, after spending close on 20 hours working on the problem (with no end in sight).

Good luck, and remember, post specific instructions for your hardware in a new thread so that others can benefit!

---

### Post by tnic on 2007-05-22
Congratulations! You prove that it is in fact possible to change resolution on an external monitor. That is inspiring for me who has spent more than 20 hours without results.

I can't find the modeline info in Xorg.0.log. 

When I switch to external monitor at boot time I get only 648x480 pixels. When I switch after startup I get 1280x800. My goal is 1280x1024.

Please look at [this](http://ubuntuforums.org/showthread.php?t=450638&page=1) thread if you have any suggestions to what I shall do.

---

### Post by garba on 2007-05-24
this should be posted in the linux desktop readiness thread

congratulations for getting it to work, but having to go through this hassle in 2007 is embarassing to say the least

---

### Post by capdog on 2007-05-24
> **garba said:**
> this should be posted in the linux desktop readiness thread

congratulations for getting it to work, but having to go through this hassle in 2007 is embarassing to say the least

I know, but there's a great sense of satisfaction at the end! 

It should be sorted out in the next release of X.org 7.3 which will apparently allow for hot-plug configuration of monitors.

---

### Post by tnic on 2007-05-25
> **capdog said:**
> 
It should be sorted out in the next release of X.org 7.3 which will apparently allow for hot-plug configuration of monitors.

Do you have a release date?

---

### Post by capdog on 2007-05-28
> **tnic said:**
> Do you have a release date?

Nope, tried to find one but can't see it anywhere on the x.org website.

---

### Post by eklitzke on 2007-06-11
Xorg 7.3 will be released sometime in August, so you can expect it in Gutsy. As far as I know, however, the autoconfiguration stuff is orthogonal to the issues with this monitor -- the problems are with the i810 driver itself, not X11.

---

### Post by NOOBPLUSPLUS on 2007-11-09
I specifically joined Ubuntu to thank Capdog for finally solving this problem for me.  What a nightmare it has been.  The key for me was changing the specific 3a 4b and 5a lines.  I had just about everything else in place, but was missing that link.

Thank you Capdog!!!

I got this going on RHEL 4 on a Lenovo ThinkCentre M52 8212 system
with the following chipset details (output from lspci)
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

I have just a couple of changes/additions from Capdog's details:
1) After restarting with the monitor plugged in, I got nothing in Xorg.0.log.  So I just cut and pasted the lines from Capdog's post and they worked.  
2) I never found a 915resolution text file to edit.  I simply put the 915resolution commands at the end of rc.local immediately.
3) I modified /boot/grub/grub.conf and removed  'rhgb' from the kernel lines to prevent graphical booting (which I don't want anyway).  I think this helps ensure that the 915resolution commands in rc.local are run before X.  Maybe this isn't necessary, but it worked for me.

---

### Post by capdog on 2007-12-15
No problemo Noobplusplus, glad it worked!

---

