---
title: "Resolution problems with xorg.conf"
date: 2010-08-12
forum: Multimedia Software
---

### Post by domdest on 2010-08-12
Hello everyone! I am a new Linux user who recently installed Lucid Lynx on my home desktop, which is about 4 years old. This system uses an ATI Radeon X1600 Pro video card, and I've been having some trouble with the drivers.

All I'm interested in doing (so far) is getting my resolution from the standard 1024x768 to 1440x900. Here's what I've done so far:

1. I read through some of the forums and consulted with a friend, which led to setting up the xorg.conf file seen below:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"radeon"
EndSection

Section "Monitor"
	# HorizSync source: edid, VertRefresh source: edid
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30.0 - 82.0
	VertRefresh	50.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

What this accomplished was that now my system loads the appropriate resolution up to the login screen, then as soon as I log in it reverts to 1024x768. Another forum's thread reporting a similar problem mentioned that there could be some conflict in the Gnome session that is causing the resolution to revert; it mentions something about deleting some files from gconf etc. I couldn't make heads or tails of what I was supposed to do.

Can anyone shed more light on this problem? I greatly appreciate it.

---

### Post by Yellow Pasque on 2010-08-12
post /var/log/Xorg.0.log

---

### Post by domdest on 2010-08-12
Here you go, thanks for taking a look at it. :)

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux destefano-home 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 05:14:15 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.32-24-generic root=/dev/mapper/destefano--home-root ro quiet splash
Build Date: 16 June 2010  09:34:29AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Aug 12 00:17:23 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
Parse error on line 19 of section Screen in file /etc/X11/xorg.conf
	"modeline" is not a valid keyword in this section.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```

---

### Post by Yellow Pasque on 2010-08-12
Hmmm. This one has 'troll' written all over it.

---

### Post by domdest on 2010-08-12
Eheh, more like "noob"...I think the log I posted was a log from earlier today and it didn't update. I don't know.

Anyway my friend who is a Linux genius helped me solve the problem...I switched to the ati driver and for some reason it kicked on, even though it didn't want to work under the ati driver a few days ago.

I literally started using Linux last week, so I'm barely cruising by on what I can find in forums like this one.

Edit: for posterity, in case future noobs like me go searching and find this page, here's my current xorg.conf that seems to be working:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"ati"
EndSection

Section "Monitor"
	# HorizSync source: edid, VertRefresh source: edid
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30.0 - 82.0
	VertRefresh	50.0 - 75.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

