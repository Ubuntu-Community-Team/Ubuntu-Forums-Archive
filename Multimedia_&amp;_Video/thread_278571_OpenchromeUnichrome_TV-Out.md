---
title: "Openchrome/Unichrome TV-Out"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by lilaundgelb on 2006-10-16
I have a Via epia motherboard with integrated unichrome graphics and am using the openchrome video driver. I can arrange my xorg.conf so that either my TV-Out (via S-video) or my monitor output (VGA) is working fine, but when I try to use both together I can only get 720x480 resolution, the TV display is okay but the monitor only displays part of the screen.

Has anyone been able to get both TV and VGA outputs to work simultaneously using the openchrome or unichrome driver?

---

### Post by pulver on 2006-10-25
I'm interested in this also. Sorry don't have any answer to your question. Do you mind sharing your xorg.conf?

---

### Post by NoWhereMan on 2006-10-27
interested too

---

### Post by lilaundgelb on 2006-10-29
Here are the relevant sections from my xorg.conf (sans keyboard/mouse/touchscreen, etc.). I'm using a SP-8000E with a 800x600 touchscreen connected via VGA.

I've previously tried to do a dual-head configuration (i.e. defining two monitors and two screens) without success. I haven't tried xinerama.


[FONT="Courier New"][SIZE="1"]Section "Module"
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

Section "Device"
	Identifier "Unichrome"
	Driver "via"
	BusID "PCI:1:0:0"
	Option "EnableAGPDMA" "True"
	Option "ActiveDevice" "CRT,TV"
	Option "TVType" "NTSC"
	Option "TVOutput" "S-Video"
EndSection

Section "Monitor"
	Identifier "Microtouch"
	HorizSync 28-40
	VertRefresh 59-71
	Option "DPMS"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Unichrome"
	Monitor "Microtouch"
	DefaultDepth 16
	SubSection "Display"
		Depth 1
		Modes "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen0"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice 	"Touchscreen" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

[/SIZE][/FONT]

---

### Post by bihe on 2006-11-30
Hi there.

I own the same hardware - SP-8000E. I'm using only TV-OUT but the problem is, that I only get black/white output for PAL. I've configured everything for PAL usage - BIOS > xorg but it's no use - just black/white. Does your TV-OUT show colors?

---

### Post by ahaslam on 2006-11-30
Did you know that Via has finally released xorg7/7.1 drivers & utilitys? Apparently they've been tested on both Dapper & Edgy, you can get them here: [http://www.viaarena.com/default.aspx?PageID=2&OSID=25&CatID=2580](http://www.viaarena.com/default.aspx?PageID=2&OSID=25&CatID=2580)

Let us know how you get on ;)

Tony.

---

### Post by NoWhereMan on 2006-12-01
> **Anthony Haslam said:**
> Did you know that Via has finally released xorg7/7.1 drivers & utilitys? Apparently they've been tested on both Dapper & Edgy, you can get them here: [http://www.viaarena.com/default.aspx?PageID=2&OSID=25&CatID=2580](http://www.viaarena.com/default.aspx?PageID=2&OSID=25&CatID=2580)

Let us know how you get on ;)

Tony.

Oh. My. God. Do you mean I could maybe make that bastard compiz work??? ;__; :D

---

### Post by bihe on 2006-12-01
Hi,

Thanks for the hint. I tried the via drivers. Installation was quite smooth
when I told the install script to use 2.6.15-27 instead of 2.6.15-26.

Result:

Almost the same! Still black/white output and forget the performance compared to the openchrome drivers. Hmm - I will try some different BIOS settings, maybe do a BIOS upgrade?

---

### Post by ahaslam on 2006-12-01
> **NoWhereMan said:**
> Oh. My. God. Do you mean I could maybe make that bastard compiz work??? ;__; :D
I doubt that compiz would work, buy you never know. 

Regards the installation:

In addition to the listed dependencies, it also required *tofrodos*. If you have a fresh install of either 6.06.1 or 6.10 it should go smoothly. Otherwise, especially in Dapper (because of numerous updates) the installation script will require modification as mentioned in the previous post.

Did it work for me? No it didn't - I just got a blank screen, but then I have the dreaded K8(M/N)800. If you find TV-out & duel heads important it'll be worth a go. Don't let my experience put you off, the openChrome forum suggests that it does offer additional 2D functionality. 

Tony.

---

### Post by ahaslam on 2006-12-05
Has anyone seen any benefit with these drivers, or is it the same old Via tat?

Tony.

---

