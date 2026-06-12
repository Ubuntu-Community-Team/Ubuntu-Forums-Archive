---
title: "Dual monitor with ATi Radeon 9200 Pro in two HP L1950 monitors"
date: 2008-11-17
forum: Multimedia Software
---

### Post by setner on 2008-11-17
Hi everyone!

I'm trying to use Ubuntu (Intrepid Ibex) in a dual monitor setting in two brand new HP L1950 monitors. One is in VGA and the other in DVI input. 

I'm not getting good results, because the two monitors always appear in mirror mode: what I see in one is always what I see in the other, and I want the secondary monitor (DVI) to be an extension of the primary monitor (VGA).

Right now I can't get the driver "radeon" to work with Ubuntu, "vesa" is the only one that works correctly.

Below is my xorg.conf. Can anyone help me on this one?

Best regards,

Miguel Rentes

xorg.conf:

Section "Device"
        Identifier      "0 ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Driver          "vesa"
        Busid           "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "1 ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Driver          "vesa"
        Busid           "PCI:1:0:1"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "HP L1950 VGA"
        Option          "DPMS"
        HorizSync 24-83
        VertRefresh 50-77
EndSection

Section "Monitor"
        Identifier      "HP L1950 DVI"
        Option          "DPMS"
        HorizSync 24-83
        VertRefresh 50-77
EndSection

Section "Screen"
        Identifier      "HP L1950 VGA Screen"
        Device          "0 ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Monitor         "HP L1950 VGA"
        DefaultDepth    24
        SubSection      "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "HP L1950 DVI Screen"
        Device          "1 ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Monitor         "HP L1950 DVI"
        DefaultDepth    24
        SubSection      "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "ServerFlags"
        Option "Xinerama" "ON"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0 "HP L1950 VGA Screen" 0 0
        Screen 1 "HP L1950 DVI Screen" RightOf "HP L1950 VGA Screen"
#       Option "DualHead" "true"
#       InputDevice "Generic Keyboard"
#       InputDevice "Configured Mouse"
#       InputDevice "stylus" "SendCoreEvents"
#       InputDevice "cursor" "SendCoreEvents"
#       InputDevice "eraser" "SendCoreEvents"
EndSection

---

### Post by setner on 2008-11-28
I'm feeling quite sad right now... :confused: 

When I run ATI Catalyst Control Center, I get the following error:

"There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig"

At this point I thought I really needed to run aticonfig, but got the error:

```

sudo aticonfig --initial

Uninitialised file found, configuring.
Segmentation fault

```

:(:(

I tried to install the ati driver from [here]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") (ATI Driver Installer) but with no success. When I run this script I get 

```

sudo ./ati-driver-installer-8.28.8.run 
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: unable to detect
Removing temporary directory: fglrx-install

```

So this script can't detect what is my X version and it fails miserably. 

I also tried to do as it was said in [this post]("http://ubuntuforums.org/showthread.php?p=1773710"), but I still get my two monitors mirrored (twin view) all the time I restart X. 

How is it possible to be so hard to put two new monitors working perfectly together, where one is extending the other? 

Here is my new /etc/X11/xorg.conf file:

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0 "HP L1950 VGA Screen"
        Screen 1 "HP L1950 DVI Screen" LeftOf "HP L1950 VGA Screen"
        InputDevice     "Keyboard0" "CoreKeyboard"
        InputDevice     "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
        Load "dbe"
        Load "extmod"
        Load "freetype"
        Load "glx"
EndSection

Section "ServerFlags"
        Option "Xinerama" "1"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "Protocol" "auto"
        Option          "Device" "/dev/psaux"
        Option          "Emulate3Buttons" "yes"
        Option          "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
        Identifier      "Keyboard0"
        Driver          "kbd"
EndSection

Section "Monitor"
        Identifier      "HP L1950 VGA"
        VendorName      "HP"
        ModelName       "L1950"
        HorizSync       24-83
        VertRefresh     50-77
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier      "HP L1950 DVI"
        VendorName      "HP"
        ModelName       "L1950"
        HorizSync       24-83
        VertRefresh     50-77
        Option          "DPMS"
EndSection

Section "Device"
        Identifier      "VGA"
        Driver          "vesa"
        VendorName      "ATI Technologies Inc"
        BoardName       "Radeon 9200 Pro"
        Busid           "PCI:1:0:0"
        Screen          0
        Option "MergedFB" "true"
        Option "MonitorLayout" "TMDS, CRT"
        Option "CRT2Hsync" "24-83"
        Option "CRT2VRefresh" "50-77"
        Option "OverlayOnCRTC2" "true"
        Option "CRT2Position" "LeftOf"
        Option "MetaModes" "1280x1024-1280x1024"
        Option "MergedXineramaCRT2IsScreen0" "true"
EndSection

Section "Device"
        Identifier      "DVI"
        Driver          "vesa"
        VendorName      "ATI Technologies Inc"
        BoardName       "Radeon 9200 Pro"
        Busid           "PCI:1:0:1"
        Screen          1
        Option "MergedFB" "true"
        Option "MonitorLayout" "TMDS, CRT"
        Option "CRT2Hsync" "24-83"
        Option "CRT2VRefresh" "50-77"
        Option "OverlayOnCRTC2" "true"
        Option "CRT2Position" "LeftOf"
        Option "MetaModes" "1280x1024-1280x1024"
        Option "MergedXineramaCRT2IsScreen0" "false"
EndSection

Section "Screen"
        Identifier      "HP L1950 VGA Screen"
        Device          "VGA"
        Monitor         "HP L1950 VGA"
        DefaultDepth    24
        Option          "TwinView" "0"
        SubSection      "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "HP L1950 DVI Screen"
        Device          "DVI"
        Monitor         "HP L1950 DVI"
        DefaultDepth    24
        Option          "TwinView" "0"
        SubSection      "Display"
                Depth 24
                Modes "1280x1024"
        EndSubSection
EndSection

Section "Extensions"
        Option          "Composite" "Disable"
EndSection

```

If you do have any ideas on what might be wrong, please tell me. 

I can't believe this is so dificult, and I can't seem to understand why putting two monitors in extended mode is always a major issue in Ubuntu (at least for me...). 

I'm using the new 8.10 Ubuntu with a ATI Radeon 9200 Pro (I know it's an old model, but it's what I have at work...).

Regards

---

### Post by Person98 on 2008-12-04
hi there, yeah i know setting up multimonitors is a pain, but some issues you are having, the catalyst control center will only work if fglrx is your graphics driver to enable it go to system->hardware drivers, then check off fglrx, once that is done you should be able to use the control center. Also the twinview option is only available on nvidia graphics cards, you will either need to use randr, big desktop, or xinerama. if you search these in the forums you should be able to find a good how to. if all else fails try the command: sudo dpkg-reconfigure -phigh xserver-xorg this will restore your xorg.conf to it's orignal form if you need to start from a clean slate

---

### Post by Person98 on 2008-12-11
hey there i recently found this tutorial, worked wonders for me. you could give it a look [http://wiki.debian.org/XStrikeForce/HowToRandR12]("http://wiki.debian.org/XStrikeForce/HowToRandR12")
hope it helps good luck

---

### Post by setner on 2009-09-02
Thanks for the tutorial Person98, it gave me a help on finding a solution for my problem.

What I had to do was the following:

[LIST=1]
[*]xrandr (for finding out what monitors were connected into my graphics card), which gave me the following output:
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2560 x 1024
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 380mm x 300mm
   1280x1024      60.0*+   75.0     60.0* 
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     59.9  
   720x400        70.1  
DVI-0 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 380mm x 300mm
   1280x1024      60.0*+   75.0     60.0* 
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     59.9  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)
[*]xrandr --output DVI-0 --off (to disable the DVI monitor)
[*]xrandr --output DVI-0 --auto --right-of VGA-0 (to enable the DVI monitor and to set it right of the VGA monitor)
[/LIST] 

This way I was able to finally have my dual monitor configuration. One final detail is that when I restart my machine I always have my DVI monitor mirrored from the VGA monitor. I always have to do the commands above to have my dual monitor display working. I'll try to add a script to do this for me at boot time, possibly in /etc/rc3.d, but I haven't got plenty of time to explore this solution any further. When I get some free time I'll post here in detail this workaround.

---

### Post by Jorisvh on 2010-01-28
Hi everyone

I have exact the same problem as this:

> **setner said:**
> Hi everyone!

I'm not getting good results, because the two monitors always appear in mirror mode: what I see in one is always what I see in the other, and I want the **secondary monitor (DVI) **to**[COLOR="Red"] be an extension of the primary monitor (VGA)[/COLOR]**.

Right now I can't get the driver "radeon" to work with Ubuntu, **"vesa" is the only one that works correctly.**

Below is my xorg.conf. Can anyone help me on this one?




> **setner said:**
> I'm feeling quite sad right now... :confused: 

W[B]hen I run ATI Catalyst Control Center, I get the following error:

"There was a problem initializing Catalyst Control Center Linux edition. It could be caused by the following.

No ATI graphics driver is installed, or the ATI driver is not functioning properly. Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig"[/B]
Regards

I work with ubuntu 9.10 and my videocard is  ATI Radeon 9250 128 DDR + TV Out + DVI
My second monitor is connected with a DVI-D-SUB connector. 

I can't use also xrandr. See:
joris@Debcom:~$ xrandr --verbose
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 (0x44) normal (normal) 0mm x 0mm
	Identifier: 0x43
	Timestamp:  24057
	Subpixel:   unknown
	Clones:    
	CRTC:       0
	CRTCs:      0
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
  800x600 (0x44)   29.3MHz *current
        h: width   800 start    0 end    0 total  800 skew    0 clock   36.6KHz
        v: height  600 start    0 end    0 total  600           clock   61.0Hz
  640x480 (0x45)   18.4MHz
        h: width   640 start    0 end    0 total  640 skew    0 clock   28.8KHz
        v: height  480 start    0 end    0 total  480           clock   60.0Hz

On a Dutch forum you can see all what I did: [http://forum.ubuntu-nl.org/hardware-en-drivers/dual-head-radeon-9250-wel-in-suse-10-3-niet-in-%28k%29ubuntu/msg541188/#msg541188](http://forum.ubuntu-nl.org/hardware-en-drivers/dual-head-radeon-9250-wel-in-suse-10-3-niet-in-%28k%29ubuntu/msg541188/#msg541188)

What can I do more? I'm feeling very very sad!!! Please help me!

---

