---
title: "Dual Monitor Questions"
date: 2005-11-04
forum: Multimedia &amp; Video
---

### Post by jokr2thief on 2005-11-04
I've read the forums, I've looked and researched and Googled, and quite frankly, I am more than stumped.

Here's the setup... I've got a Dual-Headed GeForce 6600GT, (One Card, 2 outputs) with a similar monitor connected to each output and I want the displays to show two diffrent desktops. (Not cloned or spanned displays)

Here are the pertianant sections of my Xorg.conf:

```

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
	Screen 		0
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]_2"
	Driver		"nv"
	BusID		"PCI:2:0:0"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"One"
	Option		"DPMS"
	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
	Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
EndSection

Section "Monitor"
	Identifier	"Two"
	Option		"DPMS"
	# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
	Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"One"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]"
	Monitor		"One"
	DefaultDepth	24
	SubSection "Display"
        <Snipped for space -- Color Depth mode lines>
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Two"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 Ultra]_2"
	Monitor		"Two"
	DefaultDepth	24
	SubSection "Display"
	<Snipped -- More Mode lines>
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Twin_Layout"
	Screen "Two" 
	Screen "One" LeftOf "Two"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
EndSection

```

The lynchpin seems to be this section.

```
Section "ServerLayout"
	Identifier "Twin_Layout"
	[COLOR="Red"]Screen "Two"[/COLOR]
        InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
EndSection

```

Now take note of the line in red there.... When that value is set to "One", X boots in a single monitor mode and the following message is printed to /var/log/Xorg.log:

```
(EE) Screen Two doesn't exist: deleting placement
```

When the value is set to "Two", Xorg fails to load, and produces the following message:

```
Fatal server error:
Requested Entity already in use!
```

So if anyone sees anything I've missed, or anything I should be doing diffrently, I would appreciate the help.

---

### Post by dvejnovic on 2005-11-04
My example - may help you :cool:
```
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
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"si"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
    Identifier "device0"
    VendorName "ATI"
    BoardName "ATI Radeon"
    Driver "radeon"
    BusID "PCI:1:0:0"
    Option "DDCMode" "on"
    Option "DPMS"
    Screen 0    
EndSection

Section "Device"
    Identifier "device1"
    BoardName "ATI Radeon"    
    Driver "radeon"
    BusID "PCI:1:0:0"
    Option "DDCMode" "on"
    Option "DPMS"
    Screen 1        
EndSection

Section "Monitor"
	Identifier   "monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor 1280x1024"
	HorizSync    31.5 - 79.0
	VertRefresh  50.0 - 90.0
	Option	    "dpms"
EndSection

Section "Monitor"
	Identifier   "monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor 1024x768"
	HorizSync    31.5 - 57.0
	VertRefresh  50.0 - 70.0
	Option	    "dpms"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "device0"
    Monitor "monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1280x1024" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device "device1"
    Monitor "monitor1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
    Identifier "Multihead layout"
    InputDevice "Keyboard0" "CoreKeyboard"
    InputDevice "Mouse0" "CorePointer"
    Screen  "Screen0" 0 0
    Screen  "Screen1" LeftOf "Screen0" 
    Option	    "Xinerama" "off"
    Option	    "Clone" "on"
EndSection

```

---

### Post by jokr2thief on 2005-11-04
> Here's the setup... I've got a Dual-Headed GeForce 6600GT, (One Card, 2 outputs) with a similar monitor connected to each output and I want the displays to show two diffrent desktops. (Not cloned or spanned displays)

> My example - may help you 

Actually, it dosen't. That creates a clone display, and if you read the post, that's exactly what I didn't want.

---

### Post by dvejnovic on 2005-11-04
[QUOTE=jokr2thief]Actually, it dosen't. That creates a clone display.[/QUOTE]

No! I also have Dual-Headed Radeon 9000 card. On the first desktop I watch TV and on the second desktop I work

---

### Post by jokr2thief on 2005-11-04
[QUOTE=dvejnovic]No! I also have Dual-Headed Radeon 9000 card. On the first desktop I watch TV and on the second desktop I work[/QUOTE]

Okay, so I was wrong.. But either way, your example is almost identical to mine, and neither one of them works for my setup.

It may just be a diffrence between ATI and NVidia, though I don't know why that would make a diffrence in the grand sceme of things... But If you look at the two configs closely, they're very similar. If it didn't work when I hit it, it's not going to work when you hit it, either.

---

### Post by dvejnovic on 2005-11-04
[QUOTE=jokr2thief]
```
Fatal server error:
Requested Entity already in use!

```[/QUOTE]

You cannot use the same Identifier more then once:
- you define Identifier "One" two times (same for Identifier "Two").

This is posible reason, that your definition don't work! :razz:

---

### Post by jokr2thief on 2005-11-04
[QUOTE=dvejnovic]You cannot use the same Identifier more then once:
- you define Identifier "One" two times (same for Identifier "Two").

This is posible reason, that your definition don't work! :razz:[/QUOTE]


Well, I changed the identifiers for the Screens from "One" and "Two" to "Screen One" and "Screen Two"....

By your definition, that should fix the problem. 

But it didn't, and I'm still getting the same error.

---

### Post by dvejnovic on 2005-11-04
Try:
replace BusID "PCI:2:0:0" with BusID "PCI:1:0:0"

---

### Post by jokr2thief on 2005-11-04
[QUOTE=dvejnovic]Try:
replace BusID "PCI:2:0:0" with BusID "PCI:1:0:0"[/QUOTE]

I've tried that on both devices. That's the address of the card, and changing it makes the X server flip out... I'm also not sure why it's calling that card a PCI... It's not PCI-Express, it's AGP. I can change the ID to AGP:2:0:0, but that dosen't do anything either. It just puts me in the same boat I started in.

---

### Post by jokr2thief on 2005-11-04
Here's how I got this to work, in case anyone else has an NVidia card and experiences this problem

I found this link in another thread.

[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html]("http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html")

But that wasn't it. Those setting are correct, but you have to edit this line... 

```
Option "Metamodes" "1280x1024,1280x1024; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
```

And remove both of the modes that have NULL as second value, and then you're golden.

And thank you to the guy that wrote that How-To. If it wasn't for him, I would still be fighting with it.

---

### Post by Moire on 2006-03-02
Looking at the code there might be two problems:

1: Maybe the video card driver isn't installed properly, since it said in joker2thieve's case 

driver: "nv"

while there should be something like: 

driver:  "nvidia" 

or something similar.

2: The video card is Indetified twice; each monitor uses a different device (device[0] or device[1]). I've seen more people do this and it allways strikes me as weird. Maybe this causes a problem with this video card.

In the "how-to" example both posible problems are solved, thats why it might be working there...

I hope this helps others who encounter a similar problem....

---

