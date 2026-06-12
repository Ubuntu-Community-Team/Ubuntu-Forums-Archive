---
title: "ATI fglrx and dual head issue - fonts &amp; UI elements on both screens differ"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by kavit on 2006-01-07
I recently migrated from ubuntu to kubuntu (basically gnome to kde). I had my Dual Head working really well with gnome. I have since made no changes to the configuration. After installing kde and logging into kdm, I noticed that both desktops had different fonts. The fonts on one of the desktops were TTF fonts and on the other I had non ttf fonts with no AA. I also notices that the UI elements were being rendered differently. The window edges were a lot blurry and fuzzy on the screen with the non TTF, non AA fonts.

I used the fglrxconfig utility provided with the binary drivers to configure the dual head setup. It was working really well with ubuntu but upon switching to kubuntu the issue started to arse 

Has anyone else encountered this before? I am using the amd64 build and I am running the binary ATI fglrx drivers.

My xorg.conf is as shown under


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


#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
#    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"


#    ModulePath "/usr/X11R6/lib/modules"

EndSection


Section "ServerFlags"


EndSection




Section "Monitor"
    Identifier  "Monitor0"

EndSection


Section "Monitor"
    Identifier  "Monitor1"

EndSection




Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"


# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter connector 0"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "(null)" 
    Option "ScreenOverlap"              "0" 
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
    Option "CapabilitiesEx"             "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
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
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "yes"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:5:0:0"    # vendor=1002, device=5d4d
    Screen 0
EndSection

Section "Device"
    Identifier                          "ATI Graphics Adapter connector 1"
    Driver                              "fglrx"
    BusID "PCI:5:0:0"    # vendor=1002, device=5d4d
    Screen 1
EndSection



Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter connector 0"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

Section "Screen"
    Identifier  "Screen1"
    Device      "ATI Graphics Adapter connector 1"
    Monitor     "Monitor1"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection


Section "ServerLayout"

    Screen "Screen0"
    Screen "Screen1" LeftOf "Screen0"



    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection




---

