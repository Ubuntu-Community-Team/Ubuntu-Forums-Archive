---
title: "Blurry LCD Monitor with ATI Radeon 9800 pro"
date: 2006-10-23
forum: Multimedia &amp; Video
---

### Post by JohnBortion on 2006-10-23
I don't know if anyone else had this problem, but I had to manually change my /etc/X11/xorg.conf file in order to avoid having a blurry sony SDM-S74 TFT LCD monitor.  It's connected to an agp ATI Radeon 9800 pro graphics card.  The solution was to change the automatically detected driver to the "radeon" driver.  This isn't the whole file, the rest is unchanged:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
# On install, this was "ati" instead of "radeon"
	Driver		"radeon"
	BusID		"PCI:2:0:0"
	Option		"DDCMode"
EndSection

Section "Monitor"
	Identifier	"SDM-S74"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"SDM-S74"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

It took me a while to figure out, so I thought it might save someone some pain.  I changed the DPMS and DDCMode options several times before I messed with the driver option, so I'm not sure what they were before.  I had to mess with the DDCMode option back when I was using FreeBSD with xorg.

---

### Post by BitTwiddler on 2006-10-30
Hi,

I checked the specs on your monitor and it's native resolution is 1280x1024. So you may want to add this to x config file. This will give the best quality picture. I am assuming your monitor is this one

17-inch: Sony SDM-S74

Best regards

---

### Post by JohnBortion on 2006-11-03
I hear you, but I need things larger so that I can see them.  I should mention that I edited that part myself.  Ubuntu originally had 1280x1024 in the xconf file.  Thanks for the reply BitTwiddler.

---

### Post by sadalmelik57 on 2006-11-04
I've been having difficulty with the ATI Radeon 9800 Pro card in my Dell Dimension 8300 P4 3.06ghz 512mb 15" LCD monitor.  I've edited the xorg.conf so many times my brain has a macro recorded, but I can't get my system to boot Edgy and the xorg.conf error file indicated it was in the graphics card setup. Recently it shows nothing at all, but originally it complained about the "vesa" driver that was chosen for the video driver. 

I've changed the driver to "ati" "fglrx" "vga" and "radeon" all without success.  I've tried various guides to install the fglrx driver but that's another story.  Anyway, after reviewing your xorg.conf file and comparing it to my own, the only difference I see that I'm not sure about is the PCI 2.0.0.  Mine is PCI 1.0.0.  Would that be unique to your machine, or should I try to change mine to the same PCI as yours?

---

### Post by JohnBortion on 2006-11-05
Mine is an agp card and so is yours, I'm not sure why the PCI stuff is in there.  What does your dmesg look like?  Are there any agp errors? Is your card being detected?

---

### Post by BitTwiddler on 2006-11-12
Hi,

I understand about the resolution. You may want to try the following. Set the monitor to it's native resolution and increase the font size. This will give you the best screen with readable fonts. Hope this helps.

Best regards

---

### Post by BitTwiddler on 2006-11-12
Hi,

With regards to the radeon 9800 pro in the Dell. The PCI BusID identifies the  location of the video card, as in what slot it is located in. You can view all your devices in your system by entering the following command lspci as root. As an example my card returns the following.

02:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800  Pro]

I think this option is mostly used when you have 2 video cards in your system and you want to make sure that X understands which card comes first or when X can't locate your card.  As an example.

You have two video cards and the AGP card is connected to the monitor on the right side. So by specifying the BUSID you can insure that AGP is the monitor on the right.

If you have only one video card your should be able to comment out the line with a #. And the driver should automatically identify your video card. 

#    BusID "PCI:2:0:0"

Hope this helps and always keep a backup of your xorg.conf files


Best regards

---

