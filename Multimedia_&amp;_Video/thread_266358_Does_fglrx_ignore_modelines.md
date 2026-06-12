---
title: "Does fglrx ignore modelines?"
date: 2006-09-27
forum: Multimedia &amp; Video
---

### Post by thomas.hood on 2006-09-27
I see no hint of them even being registered in Xorg.0.log, yet other switches are.

If the driver doesn't accept modelines, is there any way to make it use custom resolutions?

Thanks,

Tom

---

### Post by Icarosaurus on 2006-11-04
:( I think that yes... fglrx ignores modelines.
I don't know what's your fglrx version, but things went fine in my Dapper (with fglrx 8.28..) and I could set my custom modelines.
I upgraded to Edgy and installed fglrx 8.30.3
When I set my custom modeline, I just have them hidden in the System Settings (I use KDE) and I cannot select them.
](*,) After lot of attempts, I gave up: I cannot use 1152x864 or 1024x768 @100Hz but only @85Hz.
Why I cannot use all the power of my LG F700P Monitor? :evil:

---

### Post by Icarosaurus on 2006-11-04
This is extracted from my own xorg.conf, for completeness' sake ...
Stuff I don't need 'cause they have no effect in my case are commented out.

```

Section "Device"
  identifier "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
  busid "PCI:2:0:0"
  driver "fglrx"
   Option       "no_accel" "no"
   Option       "no_dri" "no"
   Option       "DynamicClocks" "on"
   Option       "mtrr" "on"
   Option       "DesktopSetup" "Single"
   Option       "ScreenOverlap" "0"
   Option       "Capabilities" "0x00000000"
   Option       "CapabilitiesEx" "0x00000000"
   Option       "VideoOverlay" "on"
   Option       "OpenGLOverlay" "off"
   Option       "CenterMode" "off"
   Option       "PseudoColorVisuals" "off"
   Option       "Stereo" "off"
   Option       "StereoSyncEnable" "1"
   Option       "FSAAEnable" "no"
   Option       "FSAAScale" "1"
   Option       "FSAADisableGamma" "no"
   Option       "FSAACustomizeMSPos" "no"
   Option       "FSAAMSPosX0" "0.000000"
   Option       "FSAAMSPosY0" "0.000000"
   Option       "FSAAMSPosX1" "0.000000"
   Option       "FSAAMSPosY1" "0.000000"
   Option       "FSAAMSPosX2" "0.000000"
   Option       "FSAAMSPosY2" "0.000000"
   Option       "FSAAMSPosX3" "0.000000"
   Option       "FSAAMSPosY3" "0.000000"
   Option       "FSAAMSPosX4" "0.000000"
   Option       "FSAAMSPosY4" "0.000000"
   Option       "FSAAMSPosX5" "0.000000"
   Option       "FSAAMSPosY5" "0.000000"
   Option       "UseFastTLS" "0"
   Option       "BlockSignalsOnLock" "on"
   Option       "UseInternalAGPGART" "no"
   Option       "ForceGenericCPU" "no"
   Option       "KernelModuleParm" "agplock=0"
   Option       "PowerState" "1"

EndSection

Section "Monitor"
  identifier "F700P"
  Option	    "VendorName" "LG"
  Option	    "ModelName" "LG F700P"
  Option	    "DPMS" "true"
  #Modeline "1024x768@100" 124.84  1024 1088 1240 1528   768  768  771  817
  #Modeline "1152x864@100" 167.65  1152 1240 1448 1824   864  864  868  919
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. RV350 AP [Radeon 9600]"
  Monitor "F700P"
	DefaultDepth     24
#	SubSection "Display"
#		Depth     1
#		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth     4
#		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth     8
#		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth     15
#		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth     16
#		Modes    "1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
#	EndSubSection
#	SubSection "Display"
#		Depth     24
#		Modes    "1600x1200" "1280x1024" "1152x864@100" "1024x768@100" "832x624" "800x600" "720x400" "640x480"
#	EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "DRI"
  Mode 0666
EndSection

Section "Extensions"
  option "Composite" "disable"
EndSection

```

---

### Post by Icarosaurus on 2006-11-23
Yes...starting from 8.30, fglrx ignores modelines...
you can find a partial solution [here]("http://ubuntuforums.org/showthread.php?t=297511&highlight=ati+custom+modelines")
I still haven't tried this solution...
ATI drivers really suck!!

---

