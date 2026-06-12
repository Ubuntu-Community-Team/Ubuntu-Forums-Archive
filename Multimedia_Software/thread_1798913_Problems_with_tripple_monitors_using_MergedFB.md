---
title: "Problems with tripple monitors using MergedFB"
date: 2011-07-06
forum: Multimedia Software
---

### Post by niglas on 2011-07-06
I tried to follow [this]("http://ubuntuforums.org/showthread.php?t=221174") guide for the MergedFB with open source drivers, but I don't get it to work.


This is my screen setup: (One graphic card (AGP) for Monitor 0 and another for Monitor 1 & 2 (PCI))
```

               ________
        _____ |        | _____
       | 17" ||  19"   || 17" |
       |_____||        ||_____|
              |________|

Monitor:  1       0       2
Device:   1       0       2
Connector:VGA     VGA     DVI (with adapter to VGA)


```When applying the xorg.conf the middle screen is back, while the left and right screens show stripes with a vague ubuntu logo in the background.

xorg.conf:
```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    #Screen      1  "Screen1" LeftOf "Screen0"
    #Screen      2  "Screen2" RightOf "Screen0"
    Screen      1  "Screen2" Relative "Screen0" -1024 128
    Screen      2  "Screen1" Relative "Screen0" 1280 128
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "record"
    Load  "dbe"
    Load  "dri2"
    Load  "dri"
    Load  "glx"
    Load  "extmod"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      380   300    # mm
    Identifier   "Monitor0"
    VendorName   "ACR"
    ModelName    "Acer AL1913"
    HorizSync    30.0 - 82.0
    VertRefresh  56.0 - 76.0
    Option        "DPMS"
EndSection

Section "Monitor"
    #DisplaySize      300   230    # mm
    Identifier   "Monitor1"
    VendorName   "SAM"
    ModelName    "570B/580B TFT"
    HorizSync    30.0 - 61.0
    VertRefresh  50.0 - 75.0
    Option        "DPMS"
EndSection

Section "Monitor"
    #DisplaySize      300   230    # mm
    Identifier   "Monitor2"
    VendorName   "SAM"
    ModelName    "570B/580B TFT"
    HorizSync    30.0 - 61.0
    VertRefresh  50.0 - 75.0
    Option        "DPMS"
EndSection


Section "Device"
    Identifier  "Card0"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "RV280 [Radeon 9200 SE]"
    BusID       "PCI:1:0:0"
    #Option    "DDCMode" "True"
    Option      "MergedFB" "true"
    Option      "OverlayOnCRTC2" "true"
    Option      "MonitorLayout" "CRT"
EndSection

Section "Device"
    Identifier  "Card1"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon RV100 QY [Radeon 7000/VE]"
    BusID       "PCI:2:9:0"
    Screen      0
    #Option    "DDCMode" "True"
    Option      "MergedFB" "true"
    Option      "OverlayOnCRTC2" "true"
    Option      "MonitorLayout" "CRT"

EndSection

Section "Device"
    Identifier  "Card2"
    Driver      "radeon"
    VendorName  "ATI Technologies Inc"
    BoardName   "Radeon RV100 QY [Radeon 7000/VE]"
    BusID       "PCI:2:9:0"
    Screen      1
    #Option    "DDCMode" "True"
    Option      "MergedFB" "true"
    Option      "OverlayOnCRTC2" "true"
    Option      "MonitorLayout" "TMDS"
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Depth     24
        Virtual  1280 1024
        ViewPort 0 0
        Modes   "1280x1024"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Depth     24
        Virtual  1024 768
        ViewPort 0 0
        Modes   "1024x768"
    EndSubSection
EndSection

Section "Screen"
    Identifier "Screen2"
    Device     "Card2"
    Monitor    "Monitor2"
    SubSection "Display"
        Depth     24
        Virtual  1024 768
        ViewPort 0 0
        Modes   "1024x768"
    EndSubSection
EndSection

```I tried the suggested top aligned (LeftOf & RightOf) instead of the vertically center alignment (as my screen setup figure shows), but without success. I also tried using two monitors on the other graphic card with no difference. Any obvious flaws in the xorg.conf file?




Here's the log:
```
X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=3A0CCAB80CCA6F07 loop=/ubuntu/disks/root.disk ro quiet splash
Build Date: 19 April 2011  03:33:17PM
xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.20.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jul  5 17:37:38 2011
(++) Using config file: "/home/user/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] Kernel modesetting enabled.
```It stalls on:
```
(EE) RADEON(2): reusing fd for second head
```Some other info that might be of use:

```
user@ubuntu:/etc/X11$ sudo lshw -C display
  *-display:0
       description: VGA compatible controller
       product: RV280 [Radeon 9200 SE]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:16 memory:e0000000-e7ffffff ioport:9000(size=256) memory:fb000000-fb00ffff memory:fa000000-fa01ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV280 [Radeon 9200 SE] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm cap_list
       configuration: latency=32 mingnt=8
       resources: memory:e8000000-efffffff memory:fb010000-fb01ffff
  *-display
       description: VGA compatible controller
       product: Radeon RV100 QY [Radeon 7000/VE]
       vendor: ATI Technologies Inc
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=32 mingnt=8
       resources: irq:17 memory:f0000000-f7ffffff ioport:a400(size=256) memory:f9010000-f901ffff memory:f8000000-f801ffff

``````
user@ubuntu:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200 SE] [1002:5964] (rev 01)
02:09.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] [1002:5159]

``````
user@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1400x1050      60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1360x768       60.0  
   1280x800       74.9     59.8  
   1152x864       75.0  
   1280x768       74.9     59.9  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        75.0     72.8     72.8     66.7     60.0     59.9  
   720x400        70.1  
VGA-1 disconnected (normal left inverted right x axis y axis)
S-video disconnected (normal left inverted right x axis y axis)

```

---

