---
title: "unsuccessful at installing fglrx, at my wits end."
date: 2006-02-18
forum: Multimedia &amp; Video
---

### Post by torx on 2006-02-18
I have been trying to install fglrx for my 9600pro for almost 2 days now and still nothing comes out of it. i followed the HowTo thread in this forum and read halfway through the 75 pages of reply (although my problem was posted many a times, no answer was given) yet i am still unable to find a solution to my problem so i'm starting a thread and hopefully get some help on this.

anyway, this is a fresh installation of ubuntu breezy and i have only upgraded the kernel to 686-smp and no other change have been done. i followed the thread closely and there were no errors during the installation at all. yet when i restarted at the end of the setup, my OpenGL is still MESA 3D.

> torx@Torx:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)


there were no errrors AT ALL during the installation and everything went smoothly. i have also redone the whole HOWTO (uninstalling and reinstalling) yet the same result everytime. 

if anyone has a clue, i would be greatful.

---

### Post by torx on 2006-02-19
bump

---

### Post by newuser111 on 2006-02-19
its more useful if you post your etc/X11/xorg.conf file here

---

### Post by torx on 2006-02-19
okay, here it is.

> Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig Screen 0" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/CID"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load  "GLcore"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "A150-X2"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig Monitor 0"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
        Monitor    "A150-X2"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
SubSection "Display"
                Depth     15
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig Screen 0"
        Device     "ATI Graphics Adapter 0"
        Monitor    "aticonfig Monitor 0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection



---

### Post by jml75 on 2006-02-19
Here, I corrected your config.

Should be ok now.

If not, come back and I'll llook at it again.

> 
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"A150-X2"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"A150-X2"
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
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode 0666
EndSection


---

### Post by torx on 2006-02-20
^ Doesn't work. It boots me into console mode and says something along the lines of aticonfig device is not found.

---

### Post by jml75 on 2006-02-20
Give me more infos.

Can you copy the message and post it here?

Also, does it just stop at the console or does it go to the point where you get a blue screen from X that tells you that the x server did not start properly?

---

### Post by torx on 2006-02-21
[QUOTE=jml75]Give me more infos.

Can you copy the message and post it here?

Also, does it just stop at the console or does it go to the point where you get a blue screen from X that tells you that the x server did not start properly?[/QUOTE]

yeap, it's the blue screen from Xorg. which was why i couldnt copy any info.

---

