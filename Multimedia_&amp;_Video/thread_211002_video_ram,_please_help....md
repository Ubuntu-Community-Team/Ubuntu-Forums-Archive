---
title: "video ram, please help..."
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by hoehaver on 2006-07-07
hi, im john. i need help, i have a intel i810 chipset and i just got openGL to work. when i boot up my computer it says i only have 1mb of video ram, i need more!!, how can i accomplish this.... and also, i saw this on a web site for my video card......

The i810 uses system ram for video and 3d graphics. The X server will ordinarily reserve 4mb of ram for graphics, which is too little for an effective 3d setup. To tell the driver to use a larger amount, specify a VideoRam option in the Device section of your XF86Config file. A number between 10000 and 16384 seems adequate for most requirements. If too little memory is available for DMA buffers, back and depth buffers and textures, direct rendering will be disabled.





how do i do this??????

---

### Post by illuniel on 2006-08-02
would this be possible? I have a dell b120 and 1256 ram. Thing is, i want know how much video ram i have (although the manual says 128mb shared if system ram>512 mb) More so, can i specify the amount of shared Video Ram to ubuntu? 

I want to run G Earth smoothly as well as gl-117 and scorched 3d. This seems like an option.

---

### Post by Githlar on 2007-07-30
You can specify the amount of video RAM used in the XServer configuration:

sudo dpkg-reconfigure xserver-xorg

OR, if you don't want to go through that whole, mostly useless, process (by that I mean, using that command also lets you configure all kinds of stuff that you don't need at the moment), you can manually edit the xorg.conf file:

sudo gedit /etc/X11/xorg.conf

There, you will see a section similar to this:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
	Option		"UseFBDev"		"true"
EndSection
```

Simply add the VideoRam directive so that it looks like this:
```
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:2:0"
	VideoRam	8000
	Option		"UseFBDev"		"true"
EndSection
```

Of course, replace 8000 with whatever amount of video ram you want to use in KB.

---

