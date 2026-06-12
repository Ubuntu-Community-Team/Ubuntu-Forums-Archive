---
title: "Frequency control Sony Multiscan 17sf ii"
date: 2009-12-09
forum: Multimedia Software
---

### Post by cigtoxdoc on 2009-12-09
How do i get frequency of 60 hz?  i have confirmed frequency with monitor display.

60 Hz not in itself a problem except have frequent system crashes and openoffice.org drop-down menus will not display correctly.

John

---

### Post by cigtoxdoc on 2009-12-12
Problem partially solved.

My graphics card is a legacy Radeon RV100 QY [Radeon 7000/VE] with 32 mbyte memory.  The problems with proper rendition of the graphics for OpenOffice.org and System Monitor is noted in the Release Notes for 9.10.

However, the suggested solution did not work when I tried it.  Here is what I did (I am only user of PC so I do not have to worry about other users altering configuration files).  First, I opened a ROOT terminal window and used chmod 666 to change the file permissions on /etc/X11/xorg.conf so i could use the graphical gedit to modify the xorg.conf file.  Then I modified the file to read;

Section "Device"
	Identifier	"Configured Video Device"
	Driver "radeon"
        Option "RenderAccel" "off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

by adding the two lines under Identified "Configured Video Device"

I saved the file and restarted the PC.  The problem is solved.

John

---

