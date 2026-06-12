---
title: "ATI Radeon 9250 still not functional :("
date: 2006-05-26
forum: Multimedia &amp; Video
---

### Post by peter rus on 2006-05-26
okay, i know the ati linux support is lame, but i still want my graphics to function properly. the highest screen resolution i can get with 75hz is 1152x864. when i go higher i only have refreshrates of 60 hertz, which are too low for me :(. i have followed this howto: [clickyclickclick]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")
but still my problems are not solved. my card keeps getting detected as a 9200 which it isnt. it is a sapphire card with a ati chipset, but i dont think this is a problem :/ can anyone please help, tell me what you need to know and i'll post it.

this is my lspci:
```
0000:00:00.0 Host bridge: VIA Technologies, Inc.: Unknown device 0314
0000:00:00.1 Host bridge: VIA Technologies, Inc.: Unknown device 1314
0000:00:00.2 Host bridge: VIA Technologies, Inc.: Unknown device 2314
0000:00:00.3 Host bridge: VIA Technologies, Inc.: Unknown device 3208
0000:00:00.4 Host bridge: VIA Technologies, Inc.: Unknown device 4314
0000:00:00.7 Host bridge: VIA Technologies, Inc.: Unknown device 7314
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
0000:00:0a.0 Multimedia audio controller: Aureal Semiconductor Vortex 2 (rev fe)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
0000:00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 5940 (rev 01)

```

please remember i already have some drivers installed because i did that howto, but i dont know how to remove them, so please also tell me that.

thanks in advance :)

                                      Peter Rus

---

### Post by halfvolle melk on 2006-05-26
Hi,
My 9250 is also recognised as 9200 but it works.
This guide worked great for me (second method):
[http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide)
If you're on Dapper, use this one:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Check if it's installed correctly:
[http://wiki.cchtml.com/index.php/Frequently_Asked_Questions](http://wiki.cchtml.com/index.php/Frequently_Asked_Questions)

Afterwards, you may need to edit your xorg.conf to get the desired resolution. These bits are important (don't copy/paste this, check with google what your screen can do):
```
        Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       27-86
        VertRefresh     50-160
```
```
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
```
You can use **lspci -X** (X, not x) to check the BusID if needed. Notice where it says this in xorg.conf:
```
Section "Device"
        Identifier      "NVIDIA Corporation NV4 [RIVA TNT]"
        Driver          "nv"
        **BusID           "PCI:1:0:0"**
```

Ps. this is from my other puter, but that should make no difference.

---

### Post by peter rus on 2006-05-26
okay, somethings have changed, the ATI control utility says i have a 9250, so thats better, but at 1152x864 i have no longer 75 hertz :( what to do now?

---

### Post by halfvolle melk on 2006-05-26
What's the make and model of your screen? And what is the output of
```
cat /etc/X11/xorg.conf
```

---

### Post by Rippy on 2006-05-26
I don't have much to add, but I'll mention that my 9250 is also recognised as a 9200. What I'm having issues with is editing aticonfig... >_>

---

### Post by ProMaster on 2006-05-27
My 9250 is recognised as a 9200 as well, but it functions perfectly. I'm using the FGLRX drivers that come from Ubuntu. I installed "Linux restricted modules", "xorg-driver-fglrx" and "fglrx control" from Synaptic. Then I added the fglrx module to the /etc/modules file and edited /etc/X11/xorg.conf (the line where it said Driver "ATI" changed that into Driver "fglrx"). rebooted the system and presto....

By the way, halfvolle melk, are you aware you are using NVidia drivers in you xorg.conf?

---

### Post by peter rus on 2006-05-27
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/CID"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load  "GLcore"
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
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "PHILIPS 107E"
        HorizSync    30.0 - 90.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9200 Pro (RV280)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon 9200 Pro (RV280)"
        Monitor    "PHILIPS 107E"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection


```

---

### Post by peter rus on 2006-05-27
i've now changed my driver: ati in driver: fglrx and i am going to reboot now

---

### Post by peter rus on 2006-05-27
no result, i reverted to the xorg.conf you see above here. by the way, ati  control says i use mesa drivers for openGL. doest look good. argh. i just want a even high resolution as i had in wondoze. and a decent framerate. i want to play enemy territory, and i dont want the antinspect screensaver to have a framerate of 3 to 5 fps :( xD

---

### Post by halfvolle melk on 2006-05-27
[QUOTE=ProMaster]My 9250 is recognised as a 9200 as well[/QUOTE]
I checked it again and while lspci says it's a 9200, ATi control says it's an 9252 of th 9200 series.
> By the way, halfvolle melk, are you aware you are using NVidia drivers in you xorg.conf?
No, that was just on another machine :) just some bits of xorg that matter.

Peter, if you change this
```
SubSection "Display"
                Depth     24
                Modes    "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
```
into this
```
SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
```
you might get a higher resolution. However, if it says Mesa drivers ... did you try both methods?

---

### Post by peter rus on 2006-05-27
i've tried both methods yes. thats so strange. 

SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection

this was my previous config. had no effect either

---

### Post by peter rus on 2006-05-27
oke, this is my current config. still nothing better. it seems that those mesa drivers keep staying, or am i wrong?

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/CID"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load  "GLcore"
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
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ImPS/2"
        Option      "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
        Identifier   "PHILIPS 107E"
        HorizSync    30.0 - 90.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon 9200 Pro (RV280)"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. Radeon 9200 Pro (RV280)"
        Monitor    "PHILIPS 107E"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

---

### Post by halfvolle melk on 2006-05-27
Well, maybe you can set
```
 Option "OpenGLOverlay" "on"
```
Other than that I really wouldn't know. You could go through this thread
[http://www.ubuntuforums.org/showthread.php?t=143283](http://www.ubuntuforums.org/showthread.php?t=143283)

---

### Post by peter rus on 2006-05-27
yay! i managed to fix my resolution back to normal, using the xorg config utility and then choosing for medium advanced monitor configuration :) now i am gonna try setting ati to fglrx and then keep my monitor settings!

---

### Post by peter rus on 2006-05-29
okay, i discovered that my monitor can't get a higher resolution than that what i got now, okay, no problem. but now i still want to know if my 3d acceleration is okay, because screensavers go slow like hell (low fps!)

---

