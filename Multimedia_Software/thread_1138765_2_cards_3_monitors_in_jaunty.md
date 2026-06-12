---
title: "2 cards 3 monitors in jaunty"
date: 2009-04-26
forum: Multimedia Software
---

### Post by arazyal on 2009-04-26
Can not seem to get my multiple monitor setup to work in jaunty.  I have been seeing some bug reports that state that multiple cards in xorg 1.6 may not be possible as of now???


First the xorg.conf

```



Section "Monitor"
    Identifier    "screen1"
    Gamma    1.0
EndSection

Section "Monitor"
    Identifier    "screen2"
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "screen1"
    Device        "screen1"
    Defaultdepth    24
    Monitor        "screen1"
    #    SubSection "Display"
    #        Virtual    2560 1024
    #    EndSubSection
    SubSection "Display"
        Virtual    2560 1024
    EndSubSection
EndSection

Section "Screen"
    Identifier    "screen2"
    Device        "screen2"
    Defaultdepth    24
    Monitor        "screen2"
    SubSection "Display"
        Virtual    2560 1024
    EndSubSection
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    screen  "screen1" 0 0
    screen  "screen2" leftof "screen1"
EndSection

Section "Device"
    Identifier    "screen2"
    BusID        "PCI:4:0:0"
EndSection

Section "Device"
    Identifier    "screen1"
    BusID        "PCI:4:2:0"
    screen        0
EndSection



```Now for the log file.  I only did the first few pages.  You can see that both screens are detected.  there are no EE in the log not even a WW.

```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux meatwad 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd) 
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 26 13:46:46 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "screen1" (0)
(**) |   |-->Monitor "screen1"
(**) |   |-->Device "screen1"
(**) |-->Screen "screen2" (1)
(**) |   |-->Monitor "screen2"
(**) |   |-->Device "screen2"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI: (0@4:0:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xe8000000/134217728, 0xfe5e0000/65536, I/O @ 0x0000d800/256, BIOS @ 0x????????/131072
(--) PCI:*(0@4:2:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xe0000000/134217728, 0xfe5f0000/65536, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[b]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched radeon from file name radeon.ids
(==) Matched radeon for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 6.12.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
(II) RADEON: Driver for ATI Radeon chipsets:
        ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
        ATI Radeon Mobility X300 (M24) 3152 (PCIE),
        ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
        ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
        ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
        ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
        ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
        ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
        ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
        ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
        ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
        ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
        ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
        ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
        ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
        ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
        ATI Radeon X800PRO (R420) JI (AGP),
        ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
        ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
        ATI Radeon Mobility 9800 (M18) JN (AGP),
        ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
        ATI Radeon Mobility M7 LW (AGP),
        ATI Mobility FireGL 7800 M7 LX (AGP),
        ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
        ATI FireGL Mobility 9000 (M9) Ld (AGP),
        ATI Radeon Mobility 9000 (M9) Lf (AGP),
        ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
        ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
        ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
        ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
        ATI Radeon 9800XT NJ (AGP),
        ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
        ATI Radeon Mobility 9600 (M10) NQ (AGP),
        ATI Radeon Mobility 9600 (M11) NR (AGP),
        ATI Radeon Mobility 9600 (M10) NS (AGP),
        ATI FireGL Mobility T2 (M10) NT (AGP),
        ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
        ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
        ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
:
        ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
        ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
        ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
        ATI Radeon Mobility X300 (M22) 5460 (PCIE),
        ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
        ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
        ATI Radeon X800PRO (R423) UI (PCIE),
        ATI Radeon X800LE (R423) UJ (PCIE),
        ATI Radeon X800SE (R423) UK (PCIE),
        ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
        ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
        ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
        ATI FireGL unknown (R423) UR (PCIE),
        ATI FireGL unknown (R423) UT (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility Radeon X700 XL (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
        ATI Radeon Mobility 9100 IGP (U3) 5835,
        ATI Radeon XPRESS 200 5954 (PCIE),
        ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
        ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
        ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
        ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
        ATI Radeon XPRESS 200M 5975 (PCIE),
        ATI Radeon XPRESS 200 5A41 (PCIE),
        ATI Radeon XPRESS 200M 5A42 (PCIE),
        ATI Radeon XPRESS 200 5A61 (PCIE),
        ATI Radeon XPRESS 200M 5A62 (PCIE),
        ATI Radeon X300 (RV370) 5B60 (PCIE),
        ATI Radeon X600 (RV370) 5B62 (PCIE),
        ATI Radeon X550 (RV370) 5B63 (PCIE),
        ATI FireGL V3100 (RV370) 5B64 (PCIE),
        ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
        ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
        ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
        ATI Mobility Radeon X800 XT (M28) (PCIE),
        ATI Mobility FireGL V5100 (M28) (PCIE),
        ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
        ATI Radeon X850 XT PE (R480) (PCIE),
        ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
        ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
        ATI Radeon X850 XT (R480) (PCIE),
        ATI Radeon X800XT (R423) 5D57 (PCIE),
        ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
        ATI Radeon X700 PRO (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
        ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
        ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
        ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,

```
Screen 0 and the two monitors come on fine.  Screen 1 and the 3rd monitor never display a thing.  I can not seem to determine the cause.

---

### Post by arazyal on 2009-04-27
bump

---

### Post by Almighty on 2009-04-27
Unfortunately there are several of us who want to run 3 monitors in Jaunty. Hopefully there is a workaround for you as well as Nvidia card users.

---

### Post by arazyal on 2009-04-27
So that is correct that we can not use two cards in xorg 1.6 whether it is cause of xorg or xrandr?


should a higher version not mean more features, not less?

---

### Post by arazyal on 2009-04-29
bump 
still unable to get second card to post

Is this accurate that multiple vid cards are not working in jaunty?

---

### Post by Almighty on 2009-04-29
> **arazyal said:**
> bump 
still unable to get second card to post

Is this accurate that multiple vid cards are not working in jaunty?


Unfortunately it is accurate for users of our caliber this far. 

I myself have been successful in entering both of my video cards in xorg.conf and have the xserver recognize them. I have been able to one one card have 2 of the monitors create 1 desktop using twinview. I can also have the last monitor run it's own xserver displaying it own desktop, but that's about it.

Xinerama causes the xserver to go into a loop at start up. I have tried just about everything I can think of to have both cards cooperate but to no luck yet.

Supposedly there is a way, I'm just waiting for the word to when it's available.

---

### Post by wankel on 2009-04-29
I guess it's too late in the night for me, I'm staring at your xorg.conf, but can't find the third monitor.

Did you try mixing the positions of the graphics cards, the order in which they are called in the xorg.conf or the monitors connected to it?

It might seem silly, but way back I used to have a three monitor setup with two Matrox Milleniums and a Matrox G400 (not 4 monitor, since the TV-box never worked :-( ). I never found out how to graciously boot: one way or another it seemed that the G400 would not initialize properly. 

I would boot into a lower runlevel, run X --configure there and after that could enter a higher runlevel with no problem, having all three monitors in a Xinerama screen.

If I skipped the X --configure bit, X would not start and the whole system would freeze with no error whatsoever, no magic-SysRq or ctrl-alt-backspace to the rescue either.

It all does not seem very helpful, but there might be something in it that helps you a step.

Good luck!

---

### Post by HarshReality on 2009-06-06
Honestly I just have one card and my onboard.. both of which are nVidia. But I must admit it turns my stomach that I can only use all 3 screens only in windows :(

---

### Post by ushimitsudoki on 2009-06-06
I have 2 cards (2x8800GTS 512) and 3 monitors in Jaunty. No additional problems from earlier versions.

(No added functionality, either, for that matter.)

---

### Post by HarshReality on 2009-06-06
> **ushimitsudoki said:**
> I have 2 cards (2x8800GTS 512) and 3 monitors in Jaunty. No additional problems from earlier versions.

(No added functionality, either, for that matter.)
Correct but your cards are essentially the same source just different addressing. Im running 2 different nvidia drivers at 2 different addresses :P

---

### Post by deadguy on 2009-06-13
I had this same problem.  Apparently, Xinerama doesn't work with multiple cards in newer versions of Xorg.  I was able to get my triple head setup back by downgrading X to Hardy's version.  Here's how I did it: [http://www.softmechanics.net/Xinerama_with_Multiple_Graphics_Cards_in_Ubuntu_Jaunty]("http://www.softmechanics.net/Xinerama_with_Multiple_Graphics_Cards_in_Ubuntu_Jaunty")

Hope it helps!

---

### Post by slamhound on 2009-06-14
I have a two-card system with three monitors. I had the same problems that others have had (can't boot into X after install nvidia drivers).  I solved this by following the advice in this link:  

[http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/](http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/)

The main thing is to run nvidia-xconfig -a to configure X for multiple cards.  

Also, I think the nvidia drivers that Ubuntu supplies have a bug, so I got an error when nvidia-xconfig looked for the file: libnvidia-cfg.so.1 .  You need to create a symbolic link to the version-specific libnvidia-cfg.so.1 file (as described here:  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=505863))  It worked perfectly for me after that.

---

### Post by arazyal on 2009-07-01
I am hoping there is away todo this without having to downgrade

[http://paste.ubuntu.com/203687/](http://paste.ubuntu.com/203687/)

there is my config

one card / 2 monitors come on fine.  The 3rd card and monitor never come on.

---

### Post by HarshReality on 2009-07-01
I actually got mine going.. of course its spawning a seperate xsession. As I have my onboard card and a PCIe card (both nVidia) I simply had to set my BIOS to boot the onboard first.. once I did that I had no issues configuring all 3

*Note: No downgrade was required. Onboard is single monitor xsession, 8600 catd is dual monitors spanning an xsession

---

