---
title: "Wanting the perfect xorg.conf"
date: 2005-12-23
forum: Multimedia &amp; Video
---

### Post by azazel- on 2005-12-23
I just switched to Ubuntu full-blown, and I'm on a quest to create the perfect xorg.conf using the breezy-available ATI fglrx driver.  Hardware is a Radeon 9800 Pro running a Dell 1704 17" LCD.  I'm not interested in gaming, so I'm not concerned about the driver download from ATI.com.  I just want basic hardware acceleration, but I'd like to ensure that I'm getting the most bang for my buck in that regard.  If any gurus could look this over and see if I'm missing anything important or possibly beneficial, I'd appreciate it.  One thing I'm not sure about was the fontpath entries, if they are neccessary or not.  What I basically did with this was generate the file with fglrxconfig, and edited it using some of the info I got from the default xorg.conf that breezy generated on install.   Also wondering if there are any modules I need that aren't listed in here.

> 
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

#    FontPath   "/usr/share/X11/fonts/misc/"
#    FontPath   "/usr/share/X11/fonts/cyrillic"
#    FontPath   "/usr/share/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/share/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/share/X11/fonts/Type1/"
#    FontPath   "/usr/share/X11/fonts/CID"
#    FontPath   "/usr/share/X11/fonts/75dpi/"
#    FontPath   "/usr/share/X11/fonts/100dpi/"
    # paths to defoma fonts
#    FontPath   "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
#    FontPath   "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"

EndSection

Section "ServerFlags"

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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Monitor"
	Identifier	"DELL 1704FPV"
        HorizSync       63.73
        VertRefresh     60.00
	Option		"DPMS"

# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
EndSection


Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

    Driver      "vga"
EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
    Option "DesktopSetup"               "Single"
    Option "HSync2"                     "63.73" 
    Option "VRefresh2"                  "60.00" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x06419064"
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
    BusID "PCI:1:0:0"    # vendor=1002, device=4e48
    Screen 0
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Device      "ATI Graphics Adapter"
    Monitor     "DELL 1704FPV"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
    EndSubsection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

### EOF ###


Thanks in advance!  :)

---

### Post by afhp on 2005-12-23
You'd want to keep at least the defoma fonts and the /usr/shareX11/fonts/Type1/ one -- those are the outline (scalable) fonts managed by the debian font manager. All the other fonts above are the old X bitmap fonts (non-scalable). 

Other than that, this file looks pretty good.

---

### Post by azazel- on 2005-12-23
Apparently I'm out of the loop...I wasn't aware of the 'dpkg-reconfigure xserver-xorg' option, which seems to simply things tremendously as opposed to dealing with the fglrxconfig option.

---

### Post by oskude on 2005-12-23
[QUOTE=azazel-]...using the breezy-available ATI fglrx driver. ... I'm not interested in gaming, so I'm not concerned about the driver download from ATI.com.[/QUOTE]
i thought "xorg-driver-fglrx" = binary driver from ati ?

---

### Post by wylfing on 2005-12-23
> i thought "xorg-driver-fglrx" = binary driver from ati ?
There are ATI binary drivers in the Ubuntu repositories. I think what the OP means is that he doesn't care about having the absolute latest bleeding edge drivers direct from the ATI web site.

Somewhat related: Can anyone answer how well this conf file would work for a 9200? I am quite far from schooled in ATI (I'm an nVidia guy) but I help support machines that have ATI cards in them, mainly 9200s.

---

### Post by azazel- on 2005-12-23
[QUOTE=wylfing]There are ATI binary drivers in the Ubuntu repositories. I think what the OP means is that he doesn't care about having the absolute latest bleeding edge drivers direct from the ATI web site.

Somewhat related: Can anyone answer how well this conf file would work for a 9200? I am quite far from schooled in ATI (I'm an nVidia guy) but I help support machines that have ATI cards in them, mainly 9200s.[/QUOTE]

Exactly.  I was merely wanting to set up the Ubuntu repositories drivers, not the ones from ATI.  Last time I messed with Ubuntu was almost a year ago, and what little hair I had was being pulled out trying to get a custom refresh rate working correctly.  Apparently all the hoops I had to jump through last year aren't neccessary anymore since the 'reconfigure' method works beautifully.  

*This* specific config is set up for an LCD with a resolution of 1280x1024 and a refresh rate of 60hz, so it *might* work.

Quick question though, in the above config I posted, there is an ATI Device section, with a long series of options.  Those options are not in the 'xorg-reconfigure' created xorg.conf.   Would there be any benefit to adding that section to the 'xorg-reconfigure' created xorg.conf? 

Thanks for your help guys, I apreciate it.

---

