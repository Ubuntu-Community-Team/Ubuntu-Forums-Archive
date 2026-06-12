---
title: "Can't get direct rendering to work with my ati card."
date: 2007-01-06
forum: Multimedia &amp; Video
---

### Post by Canute on 2007-01-06
Lately I've been having some strange behaviour with my ubuntu installation. Basicly, I have to either select the "vesa" driver OR "radeon", "ati" and "fglrx" IF i also comment out "load dri". So since vesa doesn't use dri, i think it's safe to say that something is wrong with my direct rendering. My graphics card is a Radeon X800GT btw :)

To get a complete overview, I'll just tell my entire story. 
I started using ubuntu a few weeks after dapper got released, and I can fairly say that I was amazed. It all worked so splendid, the installation -perfect-. Of course, I did run into some small problems, but those where mainly due to my lack off knownledge about linux. I even got fglrx running without much hassle. 

A week after Edgy was released, I used the internal upgrader and it worked like a charm. Nothing to complain about. 

So about a month ago maybe two, a friend of mine were having some difficulties with his graphics card. So I told him we could swap, just to see if his were broken. In the meanwhile we had swapped cards, I accidently ruined my chipset fan. So I started using my laptop instead, I didn't really care much. 

Right before christmas, I got a new chipset fan, it all seemed to work but the graphics card. I was not able to get direct rendering nor nothing but mesa opengl. So I decided to format it and install edgy from scratch. To my surprise Edgy didn't recoqnize either my monitor or my gfx card correctly so I had to "safe graphics". Didn't really think about it, after all, I had never tried to install a clean edgy. I installed the drivers and everything worked like a charm. 

A few days from now, after I unplug my monitor and used it for my laptop, it refused to enter X. I didn't understand anything, so I decided to reformat. Used the Edgy cd, now, not even "safe graphics" worked, so I tried with the ubuntu dapper cd. One that I ordered for free using shipit (not the one I used when I installed for the first time). Now the dapper live-cd wouldn't boot with normal graphics (sadly I can't remember if I chose safe graphics the first time I installed it, but I highly doubt that I did). It did however boot with "safe graphics", so I installed it and after the installation tried to start with either "ati" or "radeon" driver, neither worked. After a number of tries, reconfigured the xserver, now with a low hz on the monitor. Everything worked, even the fglrx driver worked with the setting.

Because I felt rather uncomfortable with Dapper, I upgraded to Edgy. I installed cedega, and put in my Settlers 3 cd. Suddenly my monitor starts getting weird artifacts. I reboot, whatever I do the monitor is black when it's supposed to show a login screen. Unless, I disable the direct rendering, or i choose the vesa driver.

Keep in mind that I have tried a numerous amount of guides. One that even installed dri as a module for xorg (with a symlink).
What I personally think, is either (a) my graphics card is broken somehow, or (b) I have managed to do something with the direct rendering in some guide which shouldn't be done. 

[Click for my xorg.conf file]("http://canutes.net/xorg.txt")

---

### Post by pay on 2007-01-06
I have the same video card as you and edgy won't boot at all and dapper will only boot in safe graphics mode. The only thing I can think of is trying```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Canute on 2007-01-07
I executed that command, did a ctrl+alt+backspace. And to my surprise it loaded, but it didn't load the direct rendering, tried to swap with fglrx and insert the overlays, loaded again. But then, when i rebooted, it wouldn't load, black screen.

First i tried with the ati driver again, black screen.

Then with the fglrx, to my surprise it loaded. However, that was because I had forgotten to put the " Option  "Composite" "False"" in the config, so it didn't even try to load dri. So either way I don't get direct rendering.

---

### Post by Canute on 2007-01-07
Inserting this into the device section did the trick :)
```
Option      "BusType" "PCI"
```

My full xorg.conf. This is on Dapper however, so if you have the same problem in edgy you need to add the composite disable.
```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
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
	Option	    "XkbLayout" "no"
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

Section "Monitor"
	Identifier   "L1915S"
	HorizSync    30.0 - 65.0
	VertRefresh  50.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. R420 JJ [Radeon X800SE]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option      "BusType" "PCI"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. R420 JJ [Radeon X800SE]"
	Monitor    "L1915S"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```

---

