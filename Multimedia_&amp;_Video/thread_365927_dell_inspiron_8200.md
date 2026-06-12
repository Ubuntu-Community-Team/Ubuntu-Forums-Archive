---
title: "dell inspiron 8200"
date: 2007-02-20
forum: Multimedia &amp; Video
---

### Post by palm101 on 2007-02-20
I just couldn't get the external monitor working. I have tried the HOWTO for both twinview and xinemara. No luck.

Anyone have a sample xorg.conf for help me out?

---

### Post by veloce on 2007-02-21
> **palm101 said:**
> I just couldn't get the external monitor working. I have tried the HOWTO for both twinview and xinemara. No luck.

Anyone have a sample xorg.conf for help me out?

So your dell has an nvidia card?  Mine has intel, so this may be no use.  Anyway, here's what worked for me:

```
##########################################################################################
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This version by: Kerry Mayes, February 2007.
# For Dell Latitude D520 with external Viewsonic VE710b Monitor connected via docking station.
# 
# As an edited file, it will not be automatically updated on xserver-xorg package upgrades. 
#
# I have not run the following command to allow it to be automatically updated:
#   sudo dpkg-reconfigure -phigh xserver-xorg
##########################################################################################
#
# These sections have not been altered.
Section "Files"
       FontPath        "/usr/share/X11/fonts/misc"
       FontPath        "/usr/share/X11/fonts/cyrillic"
       FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
       FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
       FontPath        "/usr/share/X11/fonts/Type1"
       FontPath        "/usr/share/X11/fonts/100dpi"
       FontPath        "/usr/share/X11/fonts/75dpi"
       # path to defoma fonts
       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
       Load    "i2c"
       Load    "bitmap"
       Load    "ddc"
       Load    "dri"
       Load    "extmod"
       Load    "freetype"
       Load    "glx"
       Load    "int10"
       Load    "type1"
       Load    "vbe"
       Load    "dbe"
EndSection

Section "InputDevice"
       Identifier      "Generic Keyboard"
       Driver          "kbd"
       Option          "CoreKeyboard"
       Option          "XkbRules"      "xorg"
       Option          "XkbModel"      "pc104"
       Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
       Identifier      "Configured Mouse"
       Driver          "mouse"
       Option          "CorePointer"
       Option          "Device"                "/dev/input/mice"
       Option          "Protocol"              "ExplorerPS/2"
       Option          "ZAxisMapping"          "4 5"
       Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Driver          "synaptics"
       Option          "SendCoreEvents"        "true"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "auto-dev"
       Option          "HorizScrollDelta"      "0"
EndSection
#
##########################################################################################
#
# First device section, will control the Laptop LCD screen
Section "Device"
       Identifier      "D520 945GM 0"
       Driver "i810"
       BusID "PCI:0:2:0"
       # This next line is required for xinerama.
       Screen 0
       # It was stated somewhere that the LFP is always the second pipe. Make sure never 
       # to have a space after the "," it's interpreted as "None". 
       Option "MonitorLayout" "CRT,LFP"
       # I don't think this next line is actually required.
		 Option "DevicePresence" "on"
EndSection
#
##########################################################################################
#
# Second device section, will control the external screen 
Section "Device"
       Identifier "D520 945GM 1"
       Driver "i810"
		 # Even though there is a second pci address for the card, only this one is used for 
		 # the external monitor.  The other may be for the svideo out but that has not been
		 # confirmed.
       BusID "PCI:0:2:0"
       # This next line is required for xinerama.
       Screen 1
       # It was stated somewhere that the LFP is always the second pipe. Make sure never 
       # to have a space after the "," it's interpreted as "None". 
       Option "MonitorLayout" "CRT,LFP"
       # I don't think this next line is actually required.
		 Option "DevicePresence" "on"
EndSection
#
##########################################################################################
#
# First Monitor section, for the Laptop LCD screen.
Section "Monitor"
       Identifier      "D520 Monitor"
       # I can't find a definitive source for these values, so am not using them.
		 # HorizSync       30-64
       # VertRefresh     48-120
       DisplaySize     304 228     # From manual
       Option          "DPMS"
EndSection
#
##########################################################################################
#
# Second Monitor section, for the Viewsonic monitor connected to the docking station.
Section "Monitor"
       Identifier "Viewsonic VE710b Monitor"
       # These values are from the monitor's manual.
       HorizSync       30-82
       VertRefresh     50-75
       DisplaySize	338 270
       Option "DPMS"
EndSection
#
##########################################################################################
#
# First screen section, connects the first device to the Laptop LCD screen.
# Note that the resolution "1400x1050" wasn't available until I had installed 915resolution
Section "Screen"
       Identifier      "D520 Screen"
       Device          "D520 945GM 0"
       Monitor         "D520 Monitor"
       DefaultDepth    24
       SubSection "Display"
               Depth           24
               Modes           "1400x1050" "1280x1024"
               viewport 0 0
       EndSubSection
       SubSection "Display"
               Depth           16
               Modes           "1400x1050" "1280x1024"
               viewport 0 0
       EndSubSection
EndSection
#
##########################################################################################
#
# Second screen section, connects the second device to the Viewsonic monitor connected to 
# the docking station.
Section "Screen"
       Identifier "Viewsonic VE710b Screen"
       Device "D520 945GM 1"
       Monitor "Viewsonic VE710b Monitor"
       DefaultDepth 24
       SubSection "Display"
               Depth 24
               Modes "1280x1024" "1024x768"
               # This next line has been found useful when xinerama automatically makes 
               # the two screens the same virtual size - this command can be used on the 
               # lower resolution screen to limit it to the resolution it can display 
               # without scrolling.
               # virtual 1280 1024
               viewport 0 0
       EndSubSection
       SubSection "Display"
               Depth 16
               Modes "1280x1024" "1024x768"
               # This next line has been found useful when xinerama automatically makes 
               # the two screens the same virtual size - this command can be used on the 
               # lower resolution screen to limit it to the resolution it can display 
               # without scrolling.
               # virtual 1280 1024
               viewport 0 0
       EndSubSection
EndSection
#
##########################################################################################
#
# The serverlayout section to put it all together.  
# Currently I use this file for both Laptop only and Dual screens so have to comment things 
# out or put them back in each time I switch.
#
Section "ServerLayout"
       Identifier      "Default Layout"
       # For the Intel, having a screen number in these lines seems to get it confused.
       Screen       "D520 Screen" 0 0
       # Comment out the next two lines to use just the laptop screen.        
#       Screen       "Viewsonic VE710b Screen" LeftOf "D520 Screen"
#       Option "Xinerama" "on"
       Option "Clone" "off"
       InputDevice     "Generic Keyboard"
       InputDevice     "Configured Mouse"
       InputDevice     "Synaptics Touchpad"
EndSection
#
# Sometimes gnome remembers layout stuff that screws up the screen - you can't drag windows
# into certain parts of the screen and so forth.  The solution I found on the forums was to
# delete the following directory: [home directory]/.gconf/desktop/gnome/screen
#
#
##########################################################################################
#
# These sections not altered.
Section "ServerFlags"
EndSection

Section "DRI"
       Mode    0666
EndSection
#
##########################################################################################

```

---

### Post by palm101 on 2007-02-21
Yes. I have a Nvidia card....

---

