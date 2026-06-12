---
title: "Need help configuring: xorg.conf for VIA Epia 1000M - Composite Out"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by cjtinant on 2008-03-15
I am in need of assistance customizing the xorg.conf to work with my VIA EPIA M1000 frontend box.  Setting this up in my bedroom (13" TV).  Connecting to the Composite jacks on TV.  Audio will stream from jack and connecting via Composite cable - using an adapter at PC.  There will will not be a keyboard/mouse connected for most of the time, but would like option to have option: "#".  Below is a file I came accross that was created for "everyone" using the EPIA motherboard.  So, if you could spare the time, please help and setup the way I need it as it is greek to me...  Thanks in advance!!!

Also, not sure if this is where it needs to be done, but I would LIKE to have num-lock ON at boot and screensaver; TV goes blank after 5 or so minutes if nothing is playing. Pressing the remote will turn signal back on.


# XFree86 4 configuration created by pyxf86config
Section "ServerLayout"
Identifier "Default Layout"
Screen 0 "Screen0" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"

# RgbPath is the location of the RGB database. Note, this is the name of the 
# file minus the extension (like ".txt" or ".db"). There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)
# By default, Red Hat 6.0 and later now use a font server independent of
# the X server to render fonts.
RgbPath "/usr/X11R6/lib/X11/rgb"
FontPath "unix/:7100"
EndSection

Section "ServerFlags"
# Option "NoTrapSignals"
# Option "DontVTSwitch"
# Option "DontZap"
# Option "Dont Zoom"
# Option "DisableVidModeExtension"
# Option "AllowNonLocalXvidtune"
# Option "DisableModInDev"
# Option "AllowNonLocalModInDev"
Option "BlankTime" "0"
Option "StandbyTime" "0"
Option "SuspendTime" "0"
Option "OffTime" "0"
EndSection

Section "Module"
Load "dbe"
Load "extmod"
Load "fbdevhw"
Load "glx"
Load "record"
Load "freetype"
Load "type1"
Load "dri"
EndSection

Section "InputDevice"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
# Option "Xleds" "1 2 3"
# To disable the XKEYBOARD extension, uncomment XkbDisable.
# Option "XkbDisable"
# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults). For example, for a non-U.S.
# keyboard, you will probably want to use:
# Option "XkbModel" "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
# Option "XkbModel" "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
# Option "XkbLayout" "de"
# or:
# Option "XkbLayout" "de"
# Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
# Option "XkbOptions" "ctrl:swapcaps"
# Or if you just want both to be control, use:
# Option "XkbOptions" "ctrl:nocaps"
#
Identifier "Keyboard0"
Driver "kbd"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "IMPS/2"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
HorizSync 30.0 - 50.0
VertRefresh 50.0 - 75.0
EndSection

Section "Monitor"
Identifier "MonitorTv"
VendorName ""
ModelName "TV-NTSC"
HorizSync 24.0 - 80.0
VertRefresh 50.0 - 75.0
#Option "nodpms"
#Option "noddc"
# Set for 4:3 display
#DisplaySize 400 300
DisplaySize 400 225

#Refresh Rate 60Hz
ModeLine "720x480" 26.7 720 736 808 896 480 481 484 497
ModeLine "720x576" 32.7 720 744 816 912 576 577 580 597
ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
ModeLine "1280x768" 80.1 1280 1344 1480 1680 768 769 772 795
ModeLine "1440x1050" 126.2 1440 1536 1688 1936 1050 1051 1054 1087
#Refresh Rate 75Hz
ModeLine "720x480" 34.9 720 752 824 928 480 481 484 502
ModeLine "720x576" 42.6 720 760 832 944 576 577 580 602
ModeLine "848x480" 41.0 848 880 968 1088 480 481 484 502
ModeLine "856x480" 41.3 856 888 976 1096 480 481 484 502
ModeLine "1024x512" 53.3 1024 1072 1176 1328 512 513 516 535
ModeLine "1280x768" 103.0 1280 1360 1496 1712 768 769 772 802
ModeLine "1440x1050" 160.0 1440 1536 1696 1952 1050 1051 1054 1096
#Refresh Rate 85Hz
ModeLine "1280x768" 118.5 1280 1368 1504 1728 768 769 772 807
ModeLine "1440x1050" 184.5 1440 1544 1704 1968 1050 1051 1054 1103
ModeLine "848x480" 47.4 848 888 976 1104 480 481 484 505
EndSection

Section "Device"
Identifier "Videocard0"
Driver "via"
VendorName "Videocard vendor"
BoardName "S3 UniChrome"
Option "PciRetry" "true"
# VideoRam 32768
Option "ActiveDevice" "CRT,TV"
# Option "UseBIOS" "true"
Option "TVType" "NTSC" ## Please change this line accordingly
# Option "TVType" "PAL" ## Please change this line accordingly
Option "TVOutput" "S-Video"
Option "EnableAGPDMA" "true"
# Option "DisplaySize" "400 300"
# Option "TVOutput" "Composite"
# Option "TVOutput" "RGB"
# Option "TVVScan" "over"
# Option "TVVScan" "under"
# Option "TVDotCrawl"
# Option "DisableVQ" "true"
# Option "NoDDCValue"
# Option "HQVManualSwitch"
# Option "NoHQVVFilter"
# Option "CaptureOverScanOff"
# Option "Cap0Deinterlace" "Bob"
# Option "Cap0Deinterlace" "Weave"
# Option "Cap1Deinterlace" "Bob"
# Option "Cap1Deinterlace" "Weave"
# Option "Cap0FieldSwap"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "MonitorTv"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 16
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
# Modes "800x600" "640x480"
Modes "720x480Noscale" ## Please change this NTSC line accordingly
# Modes "720x576Noscale" ## Please change this PAL line accordingly
# Modes "720x576Over" ## Use this for CN400 chipset if X is corrupted
# Modes "720x480Over" ## Use this for CN400 chipset if X is corrupted
EndSubSection
EndSection

Section "DRI"
Group 0
Mode 0666
EndSection

---

### Post by overdrank on 2008-03-15
HI and for myself I have no experience in the VIA chipset but you may look here 
[https://help.ubuntu.com/community/UniChrome](https://help.ubuntu.com/community/UniChrome)
Good luck! :KS

---

