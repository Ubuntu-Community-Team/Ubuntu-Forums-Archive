---
title: "Using a Lilliput UM70 as a third display"
date: 2011-02-13
forum: Multimedia Software
---

### Post by NickD-NLUG on 2011-02-13
Hi,

I'm trying to use a Lilliput UM-70 monitor as my third monitor, in addition to the dual screen set up I currently have.

My xorg.conf currently looks like this:

Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "LG"
        ModelName      "W236 1V"
        HorizSync       30.0 - 96.0
        VertRefresh     50.0 - 160.0
        Option         "DPMS"
        Option         "UseEDID" "TRUE"
        Option         "UseEDIDFreqs" "TRUE"
        Option         "UseEDIDDpi" "TRUE"
EndSection
Section "Monitor"
        Identifier     "Monitor1"
        VendorName     "LG"
        ModelName      "W236 1V"
        HorizSync       30.0 - 107.0
        VertRefresh     48.0 - 160.0
        Option         "DPMS"
        Option         "UseEDID" "TRUE"
        Option         "UseEDIDFreqs" "TRUE"
        Option         "UseEDIDDpi" "TRUE"
EndSection
Section "Screen"
        Identifier     "Screen1"
        Device         "Device1"
        Monitor        "Monitor1"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option "NvAGP" "0"
Option         "metamodes" "CRT-1: 1920x1080 +0+0"
        SubSection "Display"
                Modes       "1920x1080"
                Depth       24
        EndSubSection
EndSection
Section "Screen"
        Identifier     "Screen0"
        Device         "Device0"
        Monitor        "Monitor0"
        DefaultDepth    24
        Option         "TwinView" "0"
        Option "NvAGP" "0"
        Option "DamageEvents" "True"
        Option         "metamodes" "CRT-0: 1920x1080 +0+0"
        SubSection "Display"
                Depth       24
                Modes      "1920x1080"
        EndSubSection
EndSection
Section "Module"
        Load           "dbe"
        Load           "extmod"
        Load           "freetype"
        Load           "glx"
EndSection 
Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
EndSection
Section "Device"
        Identifier     "Device0"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 8500 GT"
        BusID          "PCI:1:0:0"
        Screen          0
EndSection
Section "Device"
        Identifier     "Device1"
        Driver         "nvidia"
        VendorName     "NVIDIA Corporation"
        BoardName      "GeForce 8500 GT"
        BusID          "PCI:1:0:0"
        Screen          1
EndSection
Section "ServerFlags"
        Option         "Xinerama" "0"
        Option "IgnoreABI"  "true"
EndSection
Section "Extensions"
EndSection

To try and get the UM-70 working I added this:

Section "Monitor"
Identifier      "Monitor0"
DisplaySize     152 92
VendorName      "Lilliput"
EndSection

Section "Device"
Identifier      "Device0"
Driver          "displaylink"
Option  "fbdev" "/dev/fb0"
EndSection

Section "Screen"
Identifier      "Screen0"
Device          "Device0"
Monitor         "Monitor0"
DefaultDepth    24
SubSection "Display"
Depth   24
Option         "TwinView" "0"
Modes   "800x480"
Option         "metamodes" "CRT-0: 800x480 +0+0"
ViewPort        0 0
EndSubSection
EndSection

I changed the layout to that listed below, and moved the Lilliput device to Screen0 as the DisplayLink apparently has to be screen0 on a box with an NVIDIA card, otherwise the displaylink driver is unloaded as X starts.

Section "ServerLayout"
        Identifier     "Layout0"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" Above "Screen0"
        Screen      2  "Screen2" LeftOf "Screen1"
EndSection

Using my configuration with no mention of the UM-70 it displays a plain green screen when I turn it on.

Using my modified xorg configuration X dies:

Backtrace:
[    40.584] 0: /usr/bin/X (xorg_backtrace+0x28) [0x45c5a8]
[    40.584] 1: /usr/bin/X (0x400000+0x5a87d) [0x45a87d]
[    40.584] 2: /lib/libpthread.so.0 (0x38fb800000+0xfb40) [0x38fb80fb40]
[    40.584] 3: /usr/lib/libpixman-1.so.0 (0x3902400000+0x509e6) [0x39024509e6]
[    40.584] 4: /usr/lib/libpixman-1.so.0 (0x3902400000+0x50f0e) [0x3902450f0e]
[    40.584] 5: /usr/lib/libpixman-1.so.0 (pixman_fill+0x3d) [0x3902430acd]
[    40.584] 6: /usr/lib/xorg/modules/libfb.so (fbFill+0x30b) [0x7f0d71abda9b]
[    40.584] 7: /usr/lib/xorg/modules/libfb.so (fbPolyFillRect+0x1da) [0x7f0d71abdffa]
[    40.584] 8: /usr/bin/X (0x400000+0xdd0ad) [0x4dd0ad]
[    40.584] 9: /usr/bin/X (miPaintWindow+0x1aa) [0x45792a]
[    40.584] 10: /usr/bin/X (miWindowExposures+0xc8) [0x457e88]
[    40.584] 11: /usr/bin/X (MapWindow+0x325) [0x4262a5]
[    40.584] 12: /usr/bin/X (0x400000+0x21826) [0x421826]
[    40.584] 13: /lib/libc.so.6 (__libc_start_main+0xfe) [0x38fb01ed8e]
[    40.584] 14: /usr/bin/X (0x400000+0x21409) [0x421409]
[    40.584] Segmentation fault at address 0x7f0d7187d000
[    40.584] 
Caught signal 11 (Segmentation fault). Server aborting

This is the device in the output of "lsusb":

Bus 004 Device 002: ID 17e9:02a9 Newnham Research 

This is my nvidia card in "lspci":

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)

I have a /dev/fb0 when I turn the Lilliput screen on.

This box has been upgraded since about 7.10 I think, and is one its second or third set of monitors, so I expect the configuration is a little crufty.  Should I abandon xorg.conf altogether, and try and use the Ubuntu/Gnome gui tools to set up the monitors?  At the moment if I use "Monitors" it brings up the NVIDIA Display Settings tool, which doesn't recognise the UM-70 at all.

Alternatively my knowledge of how xorg.conf should be configured has been learnt to fix previous issues, and subsequently forgotten - should I just restart configuring xorg.conf, or is there some other magic?

Also note I'm considering jumping from GNOME to AwesomeWM, would that make it easier to integrate a third monitor in this way?

---

### Post by NickD-NLUG on 2011-11-15
Sigh.

"bump"

---

### Post by NickD-NLUG on 2011-11-15
> **NickD-NLUG said:**
> Sigh.

"bump"

Not quite worthy of "SOLVED" just yet... but running a separate Xserver on this works - see Calabraun's entry on

[http://ubuntuforums.org/showthread.php?t=1313190](http://ubuntuforums.org/showthread.php?t=1313190)

---

