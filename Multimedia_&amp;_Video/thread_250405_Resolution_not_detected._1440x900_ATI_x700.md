---
title: "Resolution not detected. 1440x900 ATI x700"
date: 2006-09-04
forum: Multimedia &amp; Video
---

### Post by a_speck on 2006-09-04
Hello friends, hope everyone is doing well.
I seem to have a problem with my fresh install of Ubuntu on my Gateway 8510GZ laptop...


**PROBLEM:**
I can't change the screen resolution to 1440x900(native) from the screen resolution prefernces panel. The resolution is not available.

I have tried to add the "1440x900" mode in the xorg config file and adding
> Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync. My methods haven't solved my problems.

*Here is a partial copy of my xorg.conf:*

> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-72
	VertRefresh	43-60	
	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Mobility X700 (RV410 PCIE)"
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
		Modes		"1440x900_60" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


](*,) I'm tired of searching for a solution, any help will be appreciated.
Thanks:)

---

### Post by a_speck on 2006-09-04
> Depth 24
Modes **"1440x900_60.00"** "1024x768" "800x600" "640x480"
EndSubSection
EndSection


I was too sleepy last night to notice I didn't have the same resolution as in:

> Modeline "1440x900_60.00" 106.47 1440...

Still doesn't work...

Is this due to the fact that the driver is VESA?

---

### Post by djRobbieF on 2006-09-04
Couldn't you just add "1440x900" (including quotes) to the front of each Modes line (not to be mistaken with Modeline)?  Without _60.00?

Example:

 SubSection "Display"
Depth 1
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
EndSection

---

### Post by breuerp on 2006-09-04
sudo ati-config --force --initial
Then reboot and make sure that your monitor is on (and selected if you have a KVM) as the machine boots.  Problem solved.

---

### Post by a_speck on 2006-09-04
I've tried to add "1440x900" to all modes, didn't work.
The command ati-config returns:
command not found...:-k  Whats a KVM?

---

### Post by djRobbieF on 2006-09-04
Quick question; I see you're using an ATI card, but you said you're using the vesa driver.  Why not install ATI's driver?  That would be a really good starting point, and then you'd get the full features of your card.

---

### Post by breuerp on 2006-09-04
KVM = Keyboard Video Mouse switch.  It's a way to have multiple computers and only one monitor/keyboard/mouse but I digress....

I recommend you install ATI's driver for Linux a good HOWTO is here:  [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by a_speck on 2006-09-05
Hey, thanks for all the help, indeed it seems logical for me to install the ATI card.  I must admit that I glimpsed at the installation of the driver, at which point fear prevented me from moving foward.  I guess I thought I could have progressed with the VESA driver...:rolleyes:  But I shall go into the belly of the beast and try to install the driver, If anything I have you guys!

Hey, thanks again for all the help.  C'ya!

---

