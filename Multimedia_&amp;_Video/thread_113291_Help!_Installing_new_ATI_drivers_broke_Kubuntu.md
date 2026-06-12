---
title: "Help! Installing new ATI drivers broke Kubuntu"
date: 2006-01-06
forum: Multimedia &amp; Video
---

### Post by hubbadub on 2006-01-06
I just followed the guide here: [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
and it seemed to work fine. At the end, I configured my system for TV-out as well using fglrxconfig. Also, beforehand, I backed up my xorg.conf as xorg.conf.bak.

Well, upon reboot I found that I broke X somehow. Right now I have boot options for the default Kubuntu 386 kernel, as well as 2.6.12.10-686 kernel. No other boot time things are installed, so my system is pretty stock.

Doing a command line "sudo dpkg-reconfigure xserver-xorg" and going back to the default ATI driver doesnt fix the problem, and neither does copying the backup I made before hand.

I do have a nifty lil free program to browse ext3 from Windows, so if an error log will help someone figure out the issue, Ill post it right up. Can anyone help me fix this please? Thanks in advance!

EDIT: Ok, I can get to a login screen. However, login fails. From a prompt, it says:
> X: warning; process set to priority -1 instead of requested priority 0
Fatal server error: Server is already active for display 0
 If this server is no longer running, remove /tmp/.X0-lock and start again

So, I go to the temp folder, and "rm .XO-lock" then run a "sudo startx" command. Login fails again, but it gives out this error message:
> xauth:  creating new authority file /home/chris/.serverauth.8055
X: warning; process set to priority -1 instead of requested priority 0
X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux ubuntu 2.6.12-10-686-smp #1 SMP Thu Dec 22 12:13:35 UTC 2005 i686
Build Date: 10 October 2005
        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-10-686-smp (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 SMP Thu Dec 22 12:13:35 UTC 2005
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan  6 04:03:45 2006
(==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0

waiting for X server to shut down

---

### Post by Zeroedout on 2006-01-06
[quote=hubbadub]I just followed the guide here: [http://ubuntuforums.org/showpost.php?p=423584]("http://ubuntuforums.org/showpost.php?p=423584")
and it seemed to work fine. At the end, I configured my system for TV-out as well using fglrxconfig. Also, beforehand, I backed up my xorg.conf as xorg.conf.bak.

Well, upon reboot I found that I broke X somehow. Right now I have boot options for the default Kubuntu 386 kernel, as well as 2.6.12.10-686 kernel. No other boot time things are installed, so my system is pretty stock.

Doing a command line "sudo dpkg-reconfigure xserver-xorg" and going back to the default ATI driver doesnt fix the problem, and neither does copying the backup I made before hand.

I do have a nifty lil free program to browse ext3 from Windows, so if an error log will help someone figure out the issue, Ill post it right up. Can anyone help me fix this please? Thanks in advance!

EDIT: Ok, I can get to a login screen. However, login fails. From a prompt, it says:
X: warning; process set to priority -1 instead of requested priority 0
Fatal server error: Server is already active for display 0
 If this server is no longer running, remove /tmp/.X0-lock and start again

So, I go to the temp folder, and "rm .XO-lock" then run a "sudo startx" command. Login fails again, but it give a much longer multiple-page error now. I will post it in a moment.[/quote]

yes, lol, the error is the key thing to post when soemthing goes wrong, or at least describe the error in some detail.

---

### Post by hubbadub on 2006-01-06
Here is my xorg.conf file:
> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"CPD-G220R"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"CPD-G220R"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
Anyone have any ideas? If I cant fix this, its back to Windows for me......

---

### Post by hubbadub on 2006-01-06
Is there another sub-forum here that this would have been better to post on? I hate to be pushy, but I really wouldnt like to have to re-format. thanks!

---

### Post by Zeroedout on 2006-01-06
okay, quite a few things you can do. First off, can you post the xorg.conf generated by fglrxconfig? what exactly went wrong when you tried to start gdm with that config? in your xorg.conf right now, change that part Driver "ati" to Driver "fglrx"  and see what happens when you start gdm (sudo /etc/init.d/gdm start). Also when you do startx, you don't have to have a sudo, just "startx" will suffice. When you change the ati to fglx, post the output of /var/log/Xorg.0.log . Or see if you can spot the error yourself. Also post the output of fglrxinfo when you have changed the ati part to fglrx.  I have the exact same video card as you, however I used a different install method. If worse comes to worse, i'll guide you through how I install the latest ati driver, but it's a tad different than the other methods.

---

