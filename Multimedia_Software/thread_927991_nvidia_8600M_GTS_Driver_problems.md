---
title: "nvidia 8600M GTS Driver problems"
date: 2008-09-23
forum: Multimedia Software
---

### Post by melenor on 2008-09-23
Alright i recently got a Dell XPS 1530, with a 8600M GTS and i decided to dual boot with ubuntu so i got it installed and working. The problem comes from when i decide to enable the nvidia drivers, i can enable them, but when i restart there is no logon screen instead there is a a line of white going down leaving black(i cant describe that good) on the bottom of the screen you can see the colors of the logon screen but it seems to be kinda messed up. i then have to boot into Recovery mode and do xfix, and then resume boot, The driver that it downloads for me is "nvidia 'new' drivers" Am i using the correct drivers? 

Thanks for any help.

---

### Post by melenor on 2008-09-23
I have tried to use the installer on there web site but it didn't do anything.

---

### Post by melenor on 2008-09-25
I have not yet found any way to fix the nvidia display driver problem any help would very much appreciated.

---

### Post by norwoods on 2008-09-25
please run the following commands in a terminal and post the result.
you will need to enter the root password after the 'sudo insmod --versionsize --version' command


cat /proc/version
Xorg -version
sudo insmod --version
size --version
make --version
gcc --version
ls /lib/libc.so.*
uname -r
ls /usr/src |grep `uname -r`

---

### Post by norwoods on 2008-09-25
also, there does not appear to be a 8600m gts, only 8600m gt or 8600m gs, although the drivers are probably the same anyway.  you might want to find some way of detecting what you really have.

---

### Post by melenor on 2008-09-25
cat /proc/version
[INDENT]Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Aug 20 22:56:21 UTC 2008[/INDENT]

Xorg -version
[INDENT]This is a pre-release version of the X server from The X.Org Foundation.
	It is not supported in any way.
	Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
	Select the "xorg" product for bugs you find in this release.
	Before reporting bugs in pre-release versions please check the
	latest version in the X.Org Foundation git repository.
	See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

	X.Org X Server 1.4.0.90
	Release Date: 5 September 2007
	X Protocol Version 11, Revision 0
	Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
	Current Operating System: Linux QWERTY 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686
	Build Date: 13 June 2008  01:08:21AM
	 
	[INDENT]Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
		to make sure that you have the latest version.[/INDENT][/INDENT]

sudo insmod --versionsize --version
[INDENT]insmod: can't read '--versionsize': No such file or directory[/INDENT]

make --version
[INDENT]GNU Make 3.81
	Copyright (C) 2006  Free Software Foundation, Inc.
	This is free software; see the source for copying conditions.
	There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
	PARTICULAR PURPOSE.

	This program built for i486-pc-linux-gnu[/INDENT]

gcc --version
[INDENT]gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
	Copyright (C) 2007 Free Software Foundation, Inc.
	This is free software; see the source for copying conditions.  There is NO
	warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.[/INDENT]

ls /lib/libc.so.*
[INDENT]/lib/libc.so.6[/INDENT]

uname -r
[INDENT]2.6.24-19-generic[/INDENT]

ls /usr/src |grep `uname -r`
[INDENT]linux-headers-2.6.24-19-generic[/INDENT]

---

### Post by norwoods on 2008-09-25
oops, i left out an end-of-line; it should be:

sudo insmod --version
size --version

but everything else looks ok so i do not think that is a problem.

[http://www.nvnews.net/vbulletin/showthread.php?t=119682](http://www.nvnews.net/vbulletin/showthread.php?t=119682) has links to the latest driver and README:

[ftp://download.nvidia.com/XFree86/Linux-x86/177.76/NVIDIA-Linux-x86-177.76-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-x86/177.76/NVIDIA-Linux-x86-177.76-pkg1.run)

[ftp://download.nvidia.com/XFree86/Linux-x86/177.76/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.76/README/index.html)

download driver 177.76 and put it on your Desktop.
download README if you want to but a condensed version follows:
rename the driver file to something shorter so you will not have to type as much, like: NVIDIA177.76.run
get a console with ctl-alt-F1
login
change directory with cd to your Desktop
stop the X server by running sudo /etc/init.d/gdm stop
install the driver by running sudo sh NVIDIA177.76.run
answer the questions; when it asks, let it run nvidia-xconfig
reboot by running sudo shutdown -r now

---

### Post by melenor on 2008-09-25
Alright I got Good news, Bad news and weird news
good news, i got it to work, compiz-fusion runs excellent
Bad news i tried actually what you said it caused some weird problems like forcing 640x400 on me, and telling it was generic, i then tried the driver located on nvidia website version 173.14.12 which worked great
Weird thing is according to my hardware drivers i'm not using the nvidia driver, it says not in use.

---

### Post by melenor on 2008-09-25
I spoke too soon, it looks like instead of restarting completly the first time it only restarted the xserver.
After restarting i ran into the screen where it says that it is safe graphics mode, i tried enableing the Nvidia driver in the hardware driver, and then restarted but that didn't work, either i ended up doing the Xfix to be able to boot. also it seems that after starting it brings me to the text logon screen then flickers a few times and then the logon on screen appears.

---

### Post by norwoods on 2008-09-25
all that i can suggest is the troubleshooting section, Chapter 7. Frequently Asked Questions, of the README at:

[ftp://download.nvidia.com/XFree86/Linux-x86/177.76/README/index.html](ftp://download.nvidia.com/XFree86/Linux-x86/177.76/README/index.html)

---

### Post by melenor on 2008-10-02
Alright I have since tried a completly new clean install but i came up with the same error, however i now have the XORG files. 
xorg.conf - that caused the problems
[INDENT]
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
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
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection[/INDENT]

xorg.conf - after xfix fixed it, and let me boot up
[INDENT]# xorg.conf (X.Org X Window System server configuration file)
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
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection[/INDENT]

---

