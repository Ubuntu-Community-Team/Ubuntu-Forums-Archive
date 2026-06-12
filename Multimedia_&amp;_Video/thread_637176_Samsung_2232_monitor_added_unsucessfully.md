---
title: "Samsung 2232 monitor added unsucessfully"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by devoncatt on 2007-12-10
Umbutu gutsy  worked great with my old LG 17 inch monitor. I added my new monitor and it will not work ( because ati driver thinks it is 4096 X 4096)y. I have an ATI 1650X with 512 MB of memory. I tried installing the ati driver with envy. No joy. I used the latest driver from amd-ati  (8.42). I used the restricted driver choice and enabled the driver. 
What has happened is the ati control panel shows the monitor as 4096X 4096?
I used the aticonfig --initial -f which read in the xorg.conf file. It worked with my old monitor.
( now I tried the same thing with a Mepis 7.0 box and it worked no problems) 

Any idea where the ati stores it's conf file and is it editable ?or any other suggestions?

What am I doing wrong  ?   I really want to use this with my umbutu box.

The xorg.conf file for the samsung monitor

 #
        Identifier   "monitor1"
        VendorName   "Samsung"
        ModelName    "Samsung SyncMaster 2232BW (Digital)"
        HorizSync    30.0 - 81.0
        VertRefresh  56.0 - 75.0
        Gamma        1
        ModeLine     "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
        ModeLine     "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
        ModeLine     "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
        ModeLine     "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
        ModeLine     "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
        ModeLine     "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
        ModeLine     "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        ModeLine     "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
        ModeLine     "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
        ModeLine     "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
        ModeLine     "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
        ModeLine     "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
        ModeLine     "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
        ModeLine     "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        ModeLine     "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
        ModeLine     "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
        ModeLine     "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        ModeLine     "1680x1050@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        ModeLine     "1680x1050@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection
        Identifier   "aticonfig-Monitor[1]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "Failsafe Device"
        Driver      "fglrx"
        BoardName   "vesa"
        BusID       "PCI:6:0:0"
EndSection

---

### Post by marinaioditerra on 2008-01-19
Hi Devon,
I have your same problem using the Samsung syncmaster 2232bw together with Ubuntu 7.10. I'm stuck at 1280x1024, I really can't go to a bettere resolution.

Maybe have you solved the problem?

Thanks
Christian

---

### Post by cor2y on 2008-01-19
I had the same problem (old Samsung SyncMaster CRT) the drivers for it are there but selecting those driver put me in safe mode regardless of what i did.
The Solution i found was to first uninstall the closed source video driver in this case ATI , reboot, reconfigure xorg.
This time keeping my monitor listed as a generic monitor but changing the screen resolutions, horizontal and vertical refresh rates to what was the default of the monitor, consult the driver cd that came with the monitor theres usually a pdf or html file with the settings or the official site .
Restart and THEN install the closed source 3d drivers and restart again.
After that it worked although it sees my monitor as a no name generic with the settings of a samsung syncmaster.
To reconfigure xorg.
```
sudo dpkg-reconfigure xserver-xorg
```If its an ATI card be sure to initial overlay after the install of the closed drivers.
```
sudo aticonfig --initial[FONT=monospace]
s[/FONT]udo aticonfig --overlay-type=Xv
```I don't know about Nvidia cards settings.
Also this is using the closed restricted drivers that come with ubuntu not the latest from ATI.

---

### Post by marinaioditerra on 2008-01-21
Thanks a lot! I''l surely try your solution and I'll let you know.

Just another little thing, do you think you can post your xorg.conf ?

Bye!
Christian

---

### Post by cor2y on 2008-01-21
ok heres my xorg.conf
```


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

    # Uncomment if you have a wacom tablet
    #    InputDevice     "stylus"    "SendCoreEvents"
    #    InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Generic Keyboard"
    Driver      "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules" "xorg"
    Option        "XkbModel" "pc105"
    Option        "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier  "Configured Mouse"
    Driver      "mouse"
    Option        "CorePointer"
    Option        "Device" "/dev/input/mice"
    Option        "Protocol" "ImPS/2"
    Option        "ZAxisMapping" "4 5"
    Option        "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier  "stylus"
    Driver      "wacom"
    Option        "Device" "/dev/input/wacom"
    Option        "Type" "stylus"
    Option        "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier  "eraser"
    Driver      "wacom"
    Option        "Device" "/dev/input/wacom"
    Option        "Type" "eraser"
    Option        "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier  "cursor"
    Driver      "wacom"
    Option        "Device" "/dev/input/wacom"
    Option        "Type" "cursor"
    Option        "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier   "Generic Monitor"
    HorizSync    30.0 - 70.0
    VertRefresh  50.0 - 160.0
    Option        "DPMS"
EndSection

Section "Device"
    Identifier  "ATI Technologies Inc R480 [Radeon X850Pro]"
    Driver      "fglrx"
    Option        "UseFBDev" "true"
    Option        "VideoOverlay" "on"
    Option        "OpenGLOverlay" "off"
    BusID       "PCI:2:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies Inc R480 [Radeon X850Pro]"
    Monitor    "Generic Monitor"
    DefaultDepth     24
    SubSection "Display"
        Modes    "1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option        "Composite" "0"
EndSection

```

Compiz is not enabled and i used the ATI drivers that come with Ubuntu and not the latest ones that enable composite.

---

### Post by marinaioditerra on 2008-01-22
Thanks for the post :),
but at what resolution are you working?

On your xorg.conf I see that the maximum resolution explicited for you card is  "1280x1024", I'd like to work at greater resolutions.

Thanks again,
bye!

---

### Post by cor2y on 2008-01-22
thats because like i said its an old Sync Master CRT.
Thats the max resolution it can support.
For your setup consult the documentation that came with the monitor to see what the max resolution is.
Don't also forget to set the correct horizontal and vertical refresh sync ranges, all this info will either be on the cd that came with the monitor or in the booklet that also shipped with it.

---

