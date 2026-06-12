---
title: "Dual Head Setup - ATI Radeon 9250"
date: 2005-12-06
forum: Multimedia &amp; Video
---

### Post by whobutdrew on 2005-12-06
I've been trying to get a dual head setup on my computer for some time now.  I'm running an ATI Radeon 9250 with the fglrx drivers already installed.  My friend and I have been trying to hack the xorg.conf file and we both swear we have it right.  Here it is in its entirety.

[[Oh btw my monitors are both Dell 17" CRTs.  One is plugged in VGA, the other to the DVI port via a VGA/DVI adapter]]

Section "dri"
    Mode 0666
EndSection
Section "Module"
    Load        "dbe"  	# Double buffer extension
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
    Load        "type1"
    Load        "freetype"
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a
EndSection
Section "Files"
    RgbPath	"/usr/X11R6/lib/X11/rgb"
EndSection

Section "ServerFlags"
EndSection
Section "InputDevice"
    Identifier	"Keyboard1"
    Driver	"kbd"
    Option "AutoRepeat" "500 30"
    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc101"
    Option "XkbLayout"	"us"
EndSection
Section "InputDevice"
    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"
EndSection

Section "Monitor"
    Identifier  "Monitor0"
	Option "DPMS"
	HorizSync	30-90
	VertRefresh	50-160

EndSection

Section "Monitor"
    Identifier  "Monitor1"
	Option "DPMS"
	HorizSync	30-90
	VertRefresh	50-160

EndSection


Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"
    Driver      "fglrx"
EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
    Option "DesktopSetup"               "0x00000200" 
    Option "MonitorLayout"		"AUTO,AUTO"
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
    Option "VideoOverlay"               "on"
    Option "OpenGLOverlay"              "off"
    Option "CenterMode"                 "off"
    Option "PseudoColorVisuals"         "off"
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:1:0:0"    # vendor=1002, device=5960
    Screen 0
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen1"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor1"
    DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

Section "ServerLayout"

    Identifier  "Server Layout"

	Option		"Clone"		"off"
	Option		"Xinerama"	"on"
	Screen	"Screen0"
	Screen	"Screen1" LeftOf "Screen0"

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"


EndSection

### EOF ###


ANY help would be appreciated.  Thanks!

---

### Post by nolodude on 2005-12-08
It says [here]("http://www.linuxquestions.org/questions/t374352.html") that you need to add another device section with same BusID and associate it to one of the screens.

---

### Post by mlomker on 2005-12-08
If you are using the [latest drivers ]("http://ubuntuforums.org/showthread.php?t=78466")the **fglrxconfig** tool will allow you to configure a variety of dual-screen setups.

---

### Post by whobutdrew on 2005-12-10
I made a copy of my device section and identified it as "ATI Graphics Adapter_1".  I put Screen 1 at the last line before the end of section and under screen1 I put the copied device identifier.  I got two blank screens.  The X server started up fine, I know, because the Ubuntu startup sound played.  But I couldn't see anything.

---

### Post by whobutdrew on 2005-12-10
Actually tried that first but no matter what I did I only got one monitor working.  Hence my posting my entire xorg.conf file, because nobody I ask can see what's wrong with it, I'm hoping someone here could.

---

### Post by Darksun on 2005-12-13
FGLRXconfig dosen't appear to do anything when I try to use Dual Screen, it tells me to restart GDM and I do that then it's still mirror screens...

---

