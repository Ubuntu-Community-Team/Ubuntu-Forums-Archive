---
title: "X-server won't start after install AMD driver"
date: 2013-03-10
forum: Multimedia Software
---

### Post by Acharn on 2013-03-10
I just installed an HIS Radeon HD 6670 graphics card. After installing the card it ran fine using the OpenGL drivers. In fact, that's what I'm using right now. I followed the installation instructions at [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). When I reboot I come up in terminal mode, there is no graphical interface. Luckily for me I used to run a FreeBSD server back when X Windows was so hard to configure we did most things at the command line anyway, so I know how to shut down or reboot from there. Anyway, when I tried to start the X server it came back with a "segmentation fault" error. I think the problem is there is no screen section in my xorg.conf file. This was created by running 'sudo aticonfig --initial" after installing the AMD driver:
```
roger@roger-Aspire-M1610:~$ cat /etc/X11/xorg.conf
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

Can you point me to a tutorial on how to configure the xorg.conf file? I used to could generate the file from the X server, but I don't recall the flag and none of those shown when I get the error message seem appropriate. Things have changed so much since I used FreeBSD I find myself in a position like  a beginner (maybe that's where I should be posting this question). I realize I'm not giving you much to work with, but I'm hoping this is a common enough problem that the fix will be well known.

---

### Post by Acharn on 2013-03-11
OK, it looks like this is the wrong forum for this question. I'm going to mark this thread[solved], even though it really isn't, and re-post the question either in Absolute Beginners or General Support.

---

