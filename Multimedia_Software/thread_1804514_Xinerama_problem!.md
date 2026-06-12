---
title: "Xinerama problem!"
date: 2011-07-14
forum: Multimedia Software
---

### Post by rhuann on 2011-07-14
Hi guys, im having a problem with Ubuntu 11.04 + Ati Radeon 6970 + Dual Monitors - LG W2252TQ and LG W2486L
resolutions and positions are ok! but RandR its not. I cant load unity, im forced to load gnome classic(no effects), when i try anything else life? Ubuntu or Gnome Classic it blinks for 3 sec and get back at logon screen, only gnome classic(no effects). when i try to load

rhuann@rhuann-ubuntu:~$ gnome-display-properties
Xlib:  extension "RANDR" missing on display ":0.0".

if i disable xinerama on xorg.conf, it load in all options (ubuntu, gnome classic) ok but my monitors only get clone, not an extended desktop!

posting some infos:

rhuann@rhuann-ubuntu:~$ X -version
```

X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux rhuann-ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=9d789f99-659b-435f-805b-5e7e0fad20b4 ro quiet splash vt.handoff=7
Build Date: 21 May 2011  11:38:35AM
xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.20.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
```


rhuann@rhuann-ubuntu:~$ lspci | grep VGA
```
01:00.0 VGA compatible controller: ATI Technologies Inc Cayman PRO [AMD Radeon 6900 Series]
```


rhuann@rhuann-ubuntu:~$ cat /etc/X11/xorg.conf
```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen       0  "Monitor 22"
	Screen       1 "Monitor 24" RightOf "Monitor 22"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "W2252TQ"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "W2486L"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1080"
	Option	    "TargetRefresh" "60"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"	
EndSection

Section "Device"
	Identifier  "Monitor 24"
	Driver      "fglrx"
	Option	    "Monitor-DFP4" "W2486L"
	BusID       "PCI:1:0:0"
	
EndSection

Section "Device"
	Identifier  "Monitor 22"
	Driver      "fglrx"
	Option	    "Monitor-DFP5" "W2252TQ"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection

Section "Screen"
	Identifier "Monitor 22"
	Device     "Monitor 22"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Monitor 24"
	Device     "Monitor 24"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```


what sould i do to get Ubuntu Unity working fine?

---

### Post by neon401 on 2011-07-14
I am having the exact same problem you described, although with a 5870. If I enable Xinerama (which is a must for my monitor setup), Ubuntu fails to load anything other than "Classic (no effects)".
It would be nice if Xinerama would support Unity so I can get the full experience of 11.04.

---

### Post by rhuann on 2011-07-14
there`s no way to have desktop extension with unit? im in unity right now but i cant drag windows to the other monitor.

---

### Post by aphatak on 2011-07-19
I have problems with Unity desktop and multi-monitor set-up:  I want to use four.  The hardware is fine - I have been using it exactly the way I want in Windows-7 and Ubuntu 10.04.2 LTS.

Unity appears to be more pain than purity - I don't think I am going to use it!

---

