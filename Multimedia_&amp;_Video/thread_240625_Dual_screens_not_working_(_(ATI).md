---
title: "Dual screens not working :( (ATI)"
date: 2006-08-21
forum: Multimedia &amp; Video
---

### Post by curuxz on 2006-08-21
Hey I have tried all kindas ways but still cant get my dual head graphics card working under ubuntu, its a Radeon VE/7000 and this is the xorg.conf file but it is just doing clone monitor and i want dual screen, 1 big desktop.

Thanks in advance for any help :)

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

 Section "Module"
     Load "dbe" # Double-Buffering Extension
     Load "v4l" # Video for Linux
     Load "extmod"
     Load "type1"
     Load "freetype"
     Load "glx"
     Load "dri"
 EndSection
 
 Section "Device"
     Identifier "device0"
     VendorName "ATI"
     BoardName "ATI Radeon"
     Driver "ati"
     BusID "PCI:1:0:0"
     Screen 0
 EndSection
 
 Section "Device"
     Identifier "device1"
     BoardName "ATI Radeon"
     Driver "ati"
     BusID "PCI:1:0:0"
     Screen 1
 EndSection
 
 Section "Monitor"
     Identifier "monitor0"
     Option "DPMS"
 EndSection
 
 Section "Monitor"
     Identifier "monitor1"
     Option "DPMS"
 EndSection
 
 Section "Screen"
     Identifier "Screen0"
     Device "device0"
     Monitor "monitor0"
     DefaultColorDepth 24
     Subsection "Display"
         Depth 24
         Virtual 1024 768
         Modes    "1024x768"
     EndSubsection
 EndSection
 
 Section "Screen"
     Identifier "Screen1"
     Device "device1"
     Monitor "monitor1"
     DefaultColorDepth 24
     Subsection "Display"
         Depth 24
         Virtual 1024 768
         Modes    "1024x768"
     EndSubsection
 EndSection
 
 Section "ServerLayout"
     Identifier "Multihead layout"
     InputDevice "Generic Keyboard" "CoreKeyboard"
     InputDevice "Configured Mouse" "CorePointer"
     Screen  "Screen0" 0 0
     Screen  "Screen1" RightOf "Screen0"
 EndSection

 Section "ServerFlags"
     Option "Xinerama" "On"
 EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Ziox on 2006-08-21
> **curuxz said:**
> Hey I have tried all kindas ways but still cant get my dual head graphics card working under ubuntu, its a Radeon VE/7000 and this is the xorg.conf file but it is just doing clone monitor and i want dual screen, 1 big desktop.

Thanks in advance for any help :)

```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

 Section "Module"
     Load "dbe" # Double-Buffering Extension
     Load "v4l" # Video for Linux
     Load "extmod"
     Load "type1"
     Load "freetype"
     Load "glx"
     Load "dri"
 EndSection
 
 Section "Device"
     Identifier "device0"
     VendorName "ATI"
     BoardName "ATI Radeon"
     Driver "ati"
     BusID "PCI:1:0:0"
     Screen 0
 EndSection
 
 Section "Device"
     Identifier "device1"
     BoardName "ATI Radeon"
     Driver "ati"
     BusID "PCI:1:0:0"
     Screen 1
 EndSection
 
 Section "Monitor"
     Identifier "monitor0"
     Option "DPMS"
 EndSection
 
 Section "Monitor"
     Identifier "monitor1"
     Option "DPMS"
 EndSection
 
 Section "Screen"
     Identifier "Screen0"
     Device "device0"
     Monitor "monitor0"
     DefaultColorDepth 24
     Subsection "Display"
         Depth 24
         Virtual 1024 768
         Modes    "1024x768"
     EndSubsection
 EndSection
 
 Section "Screen"
     Identifier "Screen1"
     Device "device1"
     Monitor "monitor1"
     DefaultColorDepth 24
     Subsection "Display"
         Depth 24
         Virtual 1024 768
         Modes    "1024x768"
     EndSubsection
 EndSection
 
 Section "ServerLayout"
     Identifier "Multihead layout"
     InputDevice "Generic Keyboard" "CoreKeyboard"
     InputDevice "Configured Mouse" "CorePointer"
     Screen  "Screen0" 0 0
     Screen  "Screen1" RightOf "Screen0"
 EndSection

 Section "ServerFlags"
     Option "Xinerama" "On"
 EndSection

Section "DRI"
	Mode	0666
EndSection

```

the only problem I see with your Xorg file...either remove(#) the virtual lines 

Or

change though lines to 2048 768

---

### Post by curuxz on 2006-08-21
> **Ziox said:**
> the only problem I see with your Xorg file...either remove(#) the virtual lines 

Or

change though lines to 2048 768

No good :(

---

### Post by SeanHodges on 2006-08-22
Cant see any obvious problems, you have 2 Module sections - should really merge them together so that you're not trying to load modules like extmod twice:
```

 Section "Module"
     Load "dbe" # Double-Buffering Extension
     Load "v4l" # Video for Linux
     Load "extmod"
     Load "type1"
     Load "freetype"
     Load "glx"
     Load "dri"
 EndSection
```

I suggest commenting out the "Virtual" resolutions (i've personally never seen those settings in a multi-head configuration)

You could try using the MergedFB flag, as far as i'm aware Xinerama should do everything on it's own, but your card might need this extra command to divide the screens properly...

Add this into both your Device sections:

```
        Option		"MergedFB"	"true"
	Option		"CRT2Position"	"RightOf"
	Option		"CRT2HSync"	"30-80"
	Option		"CRT2VRefresh"	"59-75"
	Option		"MetaModes"	"1280x1024 1024x768"
```


[http://mg.pov.lt/xorg.conf](http://mg.pov.lt/xorg.conf) (Scroll half way down the file)

Good luck,

Sean

---

