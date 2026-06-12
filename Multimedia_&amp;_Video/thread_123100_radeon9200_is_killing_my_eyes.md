---
title: "radeon9200 is killing my eyes"
date: 2006-01-29
forum: Multimedia &amp; Video
---

### Post by Familyguy on 2006-01-29
I have a samtron monitor and a radeon 9200 card and I and running ubuntu  5.10.
Two things I have noticed is that screen is somewhat blurry(readable but annoying) and the monitor is not as bright as when the pc is booted into Win98.I tried the bight/contrast setting on the monitor.
After checking the Samtron web site,I edited the xorg.conf file but it did not help.
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"S/T 77E/76E"
	Option		"DPMS"
	HorizSync	**30-70 (was 30-50)**
	VertRefresh	**50-160 (was 50-75)**
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Monitor		"S/T 77E/76E"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Any help would be appreciated.

---

### Post by Teroedni on 2006-01-29
try option

Option "UseFBDev" "false"

---

### Post by Familyguy on 2006-01-29
Teroedni
Thanks for the advice.It did make a difference.It is  not as clear as when I boot to Windows but getting there.

---

### Post by janitor_jones on 2006-01-30
hey
i have a ati 9250 pci 128mb vid card but i can't get it to work with ubuntu
how did you get yours to work. 
Just plugged in and installed drivers?
It seems like that my problem is that ubuntu does not see my pci vid card but my on board.

---

### Post by Teroedni on 2006-01-30
[QUOTE=janitor_jones]hey
i have a ati 9250 pci 128mb vid card but i can't get it to work with ubuntu
how did you get yours to work. 
Just plugged in and installed drivers?
It seems like that my problem is that ubuntu does not see my pci vid card but my on board.[/QUOTE]


You need to disable the onboard video card.
Then your new card should work well.
also your machine will be faster since it dooesnt have to share memory with the onboard graphics card.

Do you known how to disable onboard?
It should stand in your manual .

---

### Post by Familyguy on 2006-01-30
Definitely go into your bios setup and make sure your onboard adapter is disabled.
I didn't have any problem with ubuntu finding my adapter (its AGP) and installing the drivers for it during the install.
I am still not happy with the fonts but I am working on them.

---

### Post by Mickey1 on 2006-01-31
If not disabled in bios could it cause for ubuntu to freeze up during the boot up fase?

My ATI Radeon 9200 when active in bios causes to make ubuntu quit loading when it hits the starting hotplug subsystem

I dunno how to disable it in bios allthough i assume that when i switch the selection from onboard to pci should do the trick?

Cheers,

---

### Post by Teroedni on 2006-02-10
[QUOTE=Mickey1]If not disabled in bios could it cause for ubuntu to freeze up during the boot up fase?

My ATI Radeon 9200 when active in bios causes to make ubuntu quit loading when it hits the starting hotplug subsystem

I dunno how to disable it in bios allthough i assume that when i switch the selection from onboard to pci should do the trick?

Cheers,[/QUOTE]
Yes you can get frezze because of that

Do you happend to know your motherboard name?

---

