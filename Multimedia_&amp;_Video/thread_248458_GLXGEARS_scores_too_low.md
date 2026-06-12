---
title: "GLXGEARS scores too low"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by ashrack on 2006-09-01
[COLOR="Red"]glxgears (CPU usage=15%)[/COLOR]
```
691 frames in 5.0 seconds = 138.083 FPS
690 frames in 5.0 seconds = 137.880 FPS
730 frames in 5.0 seconds = 145.873 FPS
671 frames in 5.0 seconds = 134.187 FPS
671 frames in 5.0 seconds = 134.191 FPS
673 frames in 5.0 seconds = 134.594 FPS

```
[COLOR="Red"]glxgears (when I minimize it the CPU usage=100%)[/COLOR]
```
35937 frames in 5.0 seconds = 7187.289 FPS
47062 frames in 5.0 seconds = 9412.378 FPS
42984 frames in 5.0 seconds = 8588.631 FPS

```
Why is it such a HUGE difference when GLXGEARS are in front of me or when they are minimized?
ps. I also tried with 'fgl_gears' and I get the same behaviour.

[COLOR="Red"]glxinfo |grep direct[/COLOR]
```
direct rendering: Yes
```
[COLOR="Red"]fglrxinfo[/COLOR]
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 2.0.5946 (8.27.10)

```
[COLOR="Red"]xorg.conf[/COLOR]
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
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"

#	Option		"EmulateWheel"		"true"
#	Option 		"EmulateWheelButton"	"2"
#	Option		"Emulate3Buttons"	"true"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
#for IntelliMouse's 7 buttons
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7"
#a temporary workaround 4 'middle mouse button' scrool feature
EndSection

Section "Monitor"
	Identifier   "SyncMaster"
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
EndSection

Section "Device"

	#Option		"NoAccel"		"true"
	Identifier  "ATI Technologies, Inc. Radeon R350 NI [Radeon 9800]"
#	Driver      "ati"
	Option        "XaaNoOffscreenPixmaps"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:2:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. Radeon R350 NI [Radeon 9800]"
	Monitor    "SyncMaster"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1152x864" "1024x768"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection
```
*Specs are in the sig*

---

### Post by tseliot on 2006-09-01
Keep in mind that glxgears is not a benchmark.

Try to see how the driver performs in applications which use the OpenGL

---

### Post by ashrack on 2006-09-01
have any recomandatoin of OGL apps? 
I dont believe I have any installed ATM, I just know that the UBUNTU scrensaver uses 100% CPU and is very very chopy like 3FPS

---

### Post by tseliot on 2006-09-01
That might be an issue related only to the screensavers.

Try installing a game such as penguin racer (or any other 3d game) and see how it goes.

---

### Post by ashrack on 2006-09-01
It's extemly slow, around 2FPS!
I believe I have a problem

---

### Post by tseliot on 2006-09-01
> **ashrack said:**
> It's extemly slow, around 2FPS!
I believe I have a problem

I agree with you. Maybe you should try installing the latest driver (8.28 ) for your card.

---

### Post by ashrack on 2006-09-01
with the latest drivers I still get the same strange behaviour with glx_gears only showing 120FPs but OGL games run fine now. tanx

---

### Post by odelay on 2006-10-27
I'm having the same problem.  I just updated to Edgy, but never used the glxgears command before, so I can't really make comparisons.  I get around 250 with the pop-up, and around 6-7,000 when I minimize it.

fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6065 (8.29.6)
```

Even with it minimized, I feel like I should be getting a higher score with an ATI x1400.  I'm going to try out a 3d game and see how it does.

---

### Post by zba78 on 2006-10-27
I get a very similar issue wit my mobility x700. Normal screen I'm getting around 250fps, minimised I get ```
48079 frames in 5.0 seconds = 9615.626 FPS
48096 frames in 5.0 seconds = 9619.119 FPS
48095 frames in 5.0 seconds = 9618.954 FPS
48096 frames in 5.0 seconds = 9619.006 FPS
47781 frames in 5.0 seconds = 9546.458 FPS
```

Interestingly though, my 3D games (foo billiard, Neverball etc.) all work fine. That's all that really counts

---

### Post by wedge2k on 2006-11-29
I have the same problem.  I have a 6600GT NV with the latest drivers.  

wedge@chopper:~$ glxgears
4151 frames in 5.0 seconds = 830.081 FPS
3647 frames in 5.0 seconds = 727.246 FPS
2435 frames in 5.0 seconds = 486.666 FPS
3087 frames in 5.0 seconds = 617.312 FPS
4246 frames in 5.0 seconds = 849.161 FPS

Thats not minimized.. I know i've gotten this machine to pump out like 10000 frames, but for some reason its being retarted.. I thought it was cause i was using twinview, but i turned it off and still having the problem.  

Any thoughts?

---

