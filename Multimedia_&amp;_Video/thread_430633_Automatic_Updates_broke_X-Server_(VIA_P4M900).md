---
title: "Automatic Updates broke X-Server (VIA P4M900)"
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by kellner on 2007-05-02
Hi, 

I installed Ubuntu Feisty last week; the install worked very smooth (changed over from SuSE), and I was very enthusiastic - perhaps foolishly enthusiastic. This morning I did an auto-update, without really looking at what was to be updated. Now the X server is broken, and I can't fix it. 

First, I don't understand what broke X, since the update applied to these packages (from the logifle in /root/.synaptic/log): 

apport 0.76 to 0.76.1
apport-gtk, same version update
python-apport, same
python-problem-report, same
rdesktop 1.5.0-1build1 to 1.5.0-1ubuntu1

The only other thing I did in that session was to copy a *ttf file into /usr/share/fonts/truetype and adjust its file permissions. 

X crashed (no keyboard reaction left) when I ended that session, and hasn't started up ever since. 

Xorg.0.log shows as error: 

(EE) AIGLX: Screen 0 is not DRI capable

(Additional errors are shown for /dev/input/wacom, but if I remove the wacom configuration settings from xorg.conf, the AIGLX error still remains.)

I reinstalled xserver-xorg, but this didn't help. 

The relevant current settings from xorg.conf are as follows:

```


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection


Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1440" "1920x1200" "1856x1392" "1792x1344" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
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



```

The error goes away when I disable composite and take out the section on dri, but X still doesn't start up. It tries to start up for a long time (seemingly without end), and again, and again, and again, but to no avail. 

Any ideas how to fix this?

This is with an onboard VIA graphics chip, and it had previously worked with "vesa". 

Thanks in advance,

---

