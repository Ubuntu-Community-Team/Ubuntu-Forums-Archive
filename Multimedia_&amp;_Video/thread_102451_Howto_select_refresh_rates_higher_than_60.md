---
title: "Howto select refresh rates higher than 60?"
date: 2005-12-12
forum: Multimedia &amp; Video
---

### Post by rotte2 on 2005-12-12
I've just installed Ubuntu, but I would like to select a higher refresh rate than 60. My video-card is a Intel 855 GM (well it's what is stated in my xorg.conf). In my Xorg.0.log I found the following: 

(II) I810(0): Attempting to use 60.02Hz refresh for mode "1280x1024" (849)
(II) I810(0): Attempting to use 75.08Hz refresh for mode "1024x768" (845)
(II) I810(0): Attempting to use 85.14Hz refresh for mode "800x600" (843)
(II) I810(0): Attempting to use 85.01Hz refresh for mode "640x480" (841)

I would like to use refresh 85Hz in mode 1280x1024. What do I have to do? :confused:

---

### Post by frodon on 2005-12-12
Post your xorg.conf file and give us the full name of your screen.

---

### Post by rotte2 on 2005-12-12
Hi Frondon

My screen is a **Sony 400 PS** and my xorg.conf is as follows:

Section "Files"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
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
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-64
	VertRefresh	51-85
#	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
	Modeline 	"1280x1024@85" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
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

---

### Post by frodon on 2005-12-12
rotte2, i have some difficulties to find the specification of your screen, is "PS 400" the full name of your screen ?
I'm looking for the horizontal and vertical refresh rates parameters of your screen, maybe you have the specification of your screen.

---

### Post by rotte2 on 2005-12-12
Frodon, sorry, my monitor is just the "Generic monitor" in the Monitor-section. Didn't know how to modify this section, so I just tried to add the 85 Hz as refresh rate. It didn't help, that's why I tried this post.

/Rotte2

---

### Post by frodon on 2005-12-12
Ok, when i ask for your screen name i don't mean the name of the screen in ubuntu but the name written on your screen, i just want to find your screen specification on internet in order to get the parameters i'm looking for to help you.
If you're using a laptop just give me its name.

---

### Post by rotte2 on 2005-12-12
Hmm, sorry, I thought I wrote that in my initial post. My screen is a **Sony Multiscan 400 PS**

/Rotte2

---

### Post by frodon on 2005-12-12
Well i found the datasheet : [http://www.sony-cp.com/en/products/archive/datasheet/400ps.pdf](http://www.sony-cp.com/en/products/archive/datasheet/400ps.pdf)

So edit the monitor section of your xorg.conf like that : ```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
[B]HorizSync 30-94
VertRefresh 48-160[/B]
# Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
Modeline "1280x1024@85" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync
EndSection

```Then do a Ctrl+Alt+Backspace.

---

### Post by rotte2 on 2005-12-12
Hi Frodon

That did it - thanks a lot! :D

---

### Post by tarax on 2005-12-13
[QUOTE=frodon]Well i found the datasheet : [http://www.sony-cp.com/en/products/archive/datasheet/400ps.pdf](http://www.sony-cp.com/en/products/archive/datasheet/400ps.pdf)

So edit the monitor section of your xorg.conf like that : ```
Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
[B]HorizSync 30-94
VertRefresh 48-160[/B]
# Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
Modeline "1280x1024@85" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync
EndSection

```Then do a Ctrl+Alt+Backspace.[/QUOTE]
Hi,

Sorry for that one, I'm sure the answer must be available in many places :S but...
Would you mind telling us the way you find/get/devine ;) the modeline statement(s) from one screen H & V refresh rates ?

Thank u very much in advance

Tarax

---

### Post by frodon on 2005-12-13
Hi tarax,

Heimo wrote a really nice guide which contain all the needed tricks to set your display the right way, modeline generation is also explained : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

### Post by tarax on 2005-12-13
[QUOTE=frodon]Hi tarax,

Heimo wrote a really nice guide which contain all the needed tricks to set your display the right way, modeline generation is also explained : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)[/QUOTE]

wow, _that_ seems to be what I was looking for ! :O
Thx a lot for the pointer :)

Bests
Tarax

PS: Good website BTW ;)

---

