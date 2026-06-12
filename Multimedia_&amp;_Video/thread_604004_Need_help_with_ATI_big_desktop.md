---
title: "Need help with ATI big desktop"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by Jive Turkey on 2007-11-05
I have the fglrx v8.42.3 installed manually, compiz is working fine.  I've followed all of the HowTos that would have worked for me in Feisty (ie [http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)) and it all goes as it should and my xorg.conf I think looks like it should until I get to the point where you change to the doublewide resolution.  When I go to change to 3200x1200 and hit apply it crashes/restarts X and I wind up at the login screen, only to login to clone mode again.

Any suggestions greatly appreciated.

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6958 Release
```

xorg.conf (device, monitor and screen sections):
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Monitor"
	Identifier   "DELL P1110"
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver      "fglrx"
	Option	    "UseFBDev" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	Option	    "DesktopSetup" "horizontal"
	Option	    "Capabilities" "0x00000800"
	Option	    "PairModes" "1600x1200+1600x1200"
	Option	    "EnableMonitor" "crt1,crt2"
	Option	"Mode2"	"1600x1200"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor    "DELL P1110"
	DefaultDepth     24
	SubSection "Display"
		Depth 	24
		Viewport   0 0
		Modes    "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
EndSection
```

I forgot to mention Dual-Head works ok, but no 3d on either screen and compiz crashes X when activated.

---

