---
title: "Ati messed up my gamma."
date: 2005-10-22
forum: Multimedia &amp; Video
---

### Post by ebichu on 2005-10-22
After I install fglrx drivers, the gamma is really messed up (too bright), I can hardly see anything.
So is there any solution?
Happens to the one from repositories and to the one from ati.com.
Need help : )

---

### Post by mlomker on 2005-10-22
That's not the first time that I've seen this kind of post but I've never seen an answer to it.  Does the need to use other driver prevent you from just adjusting the monitor?  Granted, I'm not a video guy so I might not understand the issue entirely.

I'd recommend jumping on the [ATI forum]("http://www.rage3d.com/board"), since they are the gurus once the driver is installed.

---

### Post by akaihola on 2006-06-02
It's a known problem in the ATI proprietary fglrx driver. Primary screen goes very bright if tv out is connected. You can get correct colors by enabling the software cursor in Xorg (option SWCursor), but then the cursor leaves artifacts on the screen.

A related note: xvideo is broken in newest fglrx versions. You only see the top half of the video.

---

### Post by Tristan9669 on 2006-07-22
> **akaihola said:**
> It's a known problem in the ATI proprietary fglrx driver. Primary screen goes very bright if tv out is connected. You can get correct colors by enabling the software cursor in Xorg (option SWCursor), but then the cursor leaves artifacts on the screen.

A related note: xvideo is broken in newest fglrx versions. You only see the top half of the video.

I have this same problem. :(

---

### Post by Spankmaster79 on 2006-12-23
Same problem here. But I don't have a TV Out cable connected....... 

I'm using a Radeon 9200 SE ....:twisted: :twisted: :twisted:

Where do I set the "swcursor" option????

---

### Post by Tristan9669 on 2007-01-27
> **Spankmaster79 said:**
> Same problem here. But I don't have a TV Out cable connected....... 

I'm using a Radeon 9200 SE ....:twisted: :twisted: :twisted:

Where do I set the "swcursor" option????

```
sudo gedit /etc/X11/xorg.conf
``` 

and add

```
Option "sw_cursor"
``` in the Device section

but then the cursor gets all glitchy. Here is some screenshots
[http://img356.imageshack.us/img356/6595/adsph0.jpg](http://img356.imageshack.us/img356/6595/adsph0.jpg)
[http://img356.imageshack.us/img356/2002/jfj9.jpg](http://img356.imageshack.us/img356/2002/jfj9.jpg)

---

### Post by Steve H on 2007-02-07
> **ebichu said:**
> After I install fglrx drivers, the gamma is really messed up (too bright), I can hardly see anything.


I'm having the same problem as well. I've tried everything people are suggesting to get some sort of idea what is happening. (except the"cursor=SW" thing, why would i want to mess up one thing just to fix another??)

As far as i can tell, it only happens when the TV-out (s-video) socket is switched on during boot. If i unplug the TV-out before booting, my primary CRT monitor goes back to normal. The problem returns even if the TV-out is plugged in (before booting) but the TV is not switched on (or receiving power).

Is there anyway of editing the xorg.conf to dictate different gamma settings for each monitor? (CRT & TV)

Below is a readout from my xorg.conf, so you can have a look and see if there is anything that stands out as being setup wrong. (sorry about the length of the readout)

](*,)

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	Screen         "aticonfig-Screen[1]" Above "aticonfig-Screen[0]"
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
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
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "Gateway EV91"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Monitor    "Gateway EV91"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x450" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]"
	Device     "aticonfig-Device[1]"
	Monitor    "aticonfig-Monitor[1]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "false"
EndSection

---

### Post by Tristan9669 on 2007-02-07
I had this problem for over an year, no solution yet.........:(

---

### Post by Steve H on 2007-02-08
Tristan, What have you tried to get this working?

i suppose some sort of collaborative process of elimination might help.

My display only goes "messed up" when the s-video cable is plugged in. I have tried the "Option "sw_cursor"" fix, and that did nothing, although I'm a bit confused as to where in the Xorg.conf that is supposed to be entered.

I have tried running it with the TV switched off (even at the power supply) and still it doesn't work properly. It seems to be something about the actual cable being plugged in.....The TV picture is perfect by the way!!

I have tried various Xorg.conf configuration progs, like xorgKonf etc. but they just produce unusable conf files, and I'm worse off than I was. I have to end up copying the old xorg.conf via command line just to get a usable desktop again.

I have also tried using Xinerama and hand building the xorg.conf file, but that just causes problems due to both displays operating at different resolutions. I want my monitor (gateway ev-910) to work at 1280x1024 (32bit) and the TV to work at 1089x768 (32bit). It would seem that it doesn't like it when the dual screens are at different resolutions.

I have scoured the ATI site but they do not seem to be bothered too much about Linux users. This is really annoying me now, and is one of the major reasons for me not completely moving over to Linux and ditching Mr.Gates's bloatware, (i guess he has his uses after all). I watch a lot of films, dvds and stuff on my TV, which is piped from the PC to the TV via a s-video to SCART cable. And i really want to get it working so I can do the same using Linux, but I guess it is not to be?!

Is there some way of setting the gamma values for just the primary monitor?
And why is it only when the cable is plugged in? (it is perfect without the cable in)

Aaaargh! HELP!!

---

### Post by Steve H on 2007-02-10
I've been doing a little more messing and i have noticed that if i plug in the s-video cable immediately after the BIOS beep then i don't get the Gamma problems.....Does anyone have any idea why this is? Could it be a BIOS setting?

I'm going to investigate further and report back.

](*,)

---

### Post by Steve H on 2007-02-16
I have now given up on my ancient Radeon 9000 card, and have opted for a nice new(ish) GeForce 6200. It is definitley more compatible than ATi straight out of the box. On my old card i kept having the primary monitor view being squashed and with washed out gamma when the TV s-video was plugged in, not so with the Nvidia card. 
It took some jiggery pokery to get the driver installed and now it works fine. Now i just need to decide how to use multiple monitors, TwinView etc.

---

### Post by bruceleo on 2007-04-12
For anyone still using the Radeon card, their is a solution:

Under "Devices" set Option "VideoOverlay" to "off"

---

### Post by Computer Guru on 2007-04-24
There is a better (more compatible) fix than that even:

```
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
```

This way only OpenGL overlays will be disabled, leaving XGL overlays intact (things like MPlayer and Games make use of overlays)

Cheers!

---

### Post by balaram on 2007-05-14
I got my ATI Radeon 9250 to work perfectly with Dapper 6.6. I inserted the  line Option "sw_cursor" under devices in xorg.conf and also under devices I set   VideoOverlay "off" and OpenGLOverlay "off". After doing this both my primary monitor and TV screen look great and Mplayer is working perfectly. Right now I'm watching the Mets and Cubs on MLB.TV in full screen on the TV (20 inch flatscreen). It looks as good as my cable television set.

---

### Post by Steve H on 2007-05-15
I wish I'd known this before I went out and bought myself a new Nvidia card.

Oh well!! At least it was better than my old Radeon 9000....

:)

---

