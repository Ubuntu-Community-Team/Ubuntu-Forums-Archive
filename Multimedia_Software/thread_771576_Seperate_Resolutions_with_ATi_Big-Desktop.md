---
title: "Seperate Resolutions with ATi Big-Desktop"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Totalchaos02 on 2008-04-27
I setup my extended desktop using Big Desktop and have had a lot of success compared to where I started. However, I cannot get two separate resolutions, it will only load with them both as the same. I am trying to get a resolution of 1440x900 and 1280x1024. Here is my xorg.conf file and thank you for any advice.

```
Section "ServerLayout"
	Identifier     "Server Layout"
	Screen      0  "Screen0" 0 0
	InputDevice    "Configured Mouse" "CorePointer"
	InputDevice    "Keyboard1" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
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
	SubSection "extmod"
		Option	    "omit xfree86-dga" # don't initialise the DGA extension
	EndSubSection
	Load  "glx"
	Load  "i2c"
	Load  "bitmap"
#Load "ddc" # this is probably safe to turn on
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Keyboard1"
	Driver      "kbd"
	Option	    "AutoRepeat" "500 30"
# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
	Option	    "XkbRules" "xfree86"
	Option	    "XkbModel" "pc101"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "Name" "Razer Copperhead"
	Option	    "Vendor" "Razer"
	Option	    "CorePointer"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Device" "/dev/input/mice"
	Option	    "Buttons" "7"
	Option	    "ButtonMapping" "1 2 3 6 7 4 5"
	Option	    "Resolution" "2000"
	Option	    "SampleRate" "1000Hz"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	Option	    "DPMS"
EndSection

Section "Device"

# === Misc Options ===
	Identifier  "ATI Graphics Adapter"
	Driver      "fglrx"
	Option	    "NoDDC" # this probably isn't necessary?
# vendor=1002, device=4e45
	Option	    "no_accel" "no"
	Option	    "no_dri" "no"
	Option	    "mtrr" "off" # disable DRI mtrr mapper, driver has its own code for mtrr
	Option	    "Capabilities" "0x00008800"
# Note: When OpenGL Overlay is enabled, Video Overlay
	Option	    "VideoOverlay" "on"
# === OpenGL Overlay ===
	Option	    "OpenGLOverlay" "off"
# === Center Mode (Laptops only) ===
	Option	    "CenterMode" "off"
# === Pseudo Color Visuals (8-bit visuals) ===
	Option	    "PseudoColorVisuals" "off"
# === QBS Management ===
	Option	    "Stereo" "off"
#Option "StereoSyncEnable" "1"
	Option	    "FSAAEnable" "no"
#Option "FSAAScale" "1"
	Option	    "UseFastTLS" "2"
	Option	    "BlockSignalsOnLock" "on"
	Option	    "OverlayOnCRTC2" "0"
	Option	    "IgnoreEDID" "off"
	Option	    "HSync2" "31.5-70" #Second monitor horizontal sync
	Option	    "VRefresh2" "50-75" #Second monitor vertical sync
	Option	    "ScreenOverlap" "100" # Pixels for Overlapping. Set to 0 to disable
	Option	    "NoTV" "yes"
	Option	    "TVStandard" "NTSC-M"
	Option	    "UseInternalAGPGART" "no"
	Option	    "ForceGenericCPU" "no"
	Option	    "KernelModuleParm" "agplock=0" # AGP locked user pages: disabled
	Option	    "DesktopSetup" "horizontal"
	Option	    "ForceMonitors" "crt1,tmds1"
	Option	    "EnableMonitor" "crt1,tmds1"
	Option	    "Mode2" "1440x900,1280x1024"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 2"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "ATI Graphics Adapter"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1440x900" "1280x1024"
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "ATI Graphics Adapter 2"
	Monitor    "Monitor1"
	DefaultDepth     24
	SubSection "Display"

#Viewport 0 0
		Depth     24
		Modes    "1440x900" "1280x1024"
	EndSubSection
EndSection

Section "DRI"

# Access to OpenGL ICD is allowed for all users:
# Access to OpenGL ICD is restricted to a specific user group:
# Group 100 # users
# Mode 0660
	Mode         0666
EndSection

```

---

### Post by Totalchaos02 on 2008-04-27
Something else I noticed, if I click on the far right edge of my second screen, toward the bottom, it crashes my system. Any ideas on what might cause this?

---

### Post by Totalchaos02 on 2008-04-28
bump

---

