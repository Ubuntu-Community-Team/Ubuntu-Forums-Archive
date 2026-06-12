---
title: "Problem with fglrx driver (8.42)"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by andrebrait on 2007-11-01
Every time I try to initialize X, if I use the fglrx driver, I get a black screen and so a message from Ubuntu saying "my graphics adapter was not correctly detected" and give me three options: Configure, Shutdown and Continue. Once I click Configure, I get to the screen configuration Windows, so I reset my configurations and click OK and reboot the system.

When I try again, I get some Errors in Gnome, so I have to start a FailSafe session to get the fglrx drivers uninstalled.

I used envy to install and remove them.

I can't get the driver to work!

My system>
AMD Athlon 64 3200+
ASUS K8V-X SE
1280MB RAM (1024+256MB) DDR-400
ATi Radeon 9600XT
Two seagates HDs, PATA

---

### Post by Yellow Pasque on 2007-11-01
After you uninstall the fglrx drivers, boot back to a terminal and run the following command:

```
sudo apt-get install xorg-driver-fglrx
```

Now navigate to the directory with the ati driver file and run it:

```
sudo sh ./ati-driver-installer-8.42.3-x86.x86_64.run
```

After that's done, run:

```
sudo aticonfig --initial -f
```

Hopefully, that'll be enough to get X working. Post back with your xorg.conf and we'll work on enabling Compositing/AIGLX if needed.

---

### Post by andrebrait on 2007-11-01
I got it running by another way
There were a lot of thrash in the x.org file, so I left it... clean

Now, it looks like this:
> Section "Files"
EndSection

Section "Module"
	Load		"fglrx"
	Load		"dbe"
	Load		"extmod"
	Load		"fbdevhw"
	Load		"glx"
	Load		"record"
	Load		"freetype"
	Load		"type1"
	Load		"dri"
	Load		"GLcore"
	Load		"v4l"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"abnt2"
	Option		"XkbLayout"	"br"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Radeon 9600XT"
	Busid		"PCI:1:0:0"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Option		"MergedFB"	"off"
	Option		"LVDSBiosNativeMode"	"false"
	Option 		"RenderAccel" 	"true"
EndSection

Section "Monitor"
	Identifier	"FailsafeMonitor"
	Vendorname	"EMC"
	Modelname	"Proview SA-558"
	Option		"DPMS"
	Horizsync	30-55
	Vertrefresh	50-150
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9600XT"
	Monitor		"FailsafeMonitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1024x768"	"832x624"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"on"
EndSection

Section "Extensions"
	Option		"Composite"	"Enabled"
EndSection

Section "DRI"
	Mode	0666
EndSection

Now, I'm having another prblem: 2D performance

It's poor! I notice the Lines when scrolling down a web page and other stuff!
how can I get rid of this?

---

### Post by andrebrait on 2007-11-01
And I can't play videos anymore!

---

### Post by Yellow Pasque on 2007-11-01
Turn off desktop effects (aka eye candy). The AIGLX performance is pretty poor at this point. My X1250 wasn't quite as slow as what you're describing, but it still lagged a bit at times.

---

### Post by andrebrait on 2007-11-01
thanks!
That worked for me!

Also I got video working, thanks!

glxgears give me +- 3000FPS now :)

What version of Compiz does Gutsy have installed?

---

