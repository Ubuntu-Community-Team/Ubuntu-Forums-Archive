---
title: "Mutiple monitor support"
date: 2009-04-23
forum: Multimedia Software
---

### Post by rnjn.sinha on 2009-04-23
My travails with supporting Multiple monitors continues in 9.04. As already pointed out in [this thread]("http://ubuntuforums.org/showthread.php?t=1058961") there is still no support for multiple graphics cards in xrandr 1.3. I have the following cards on my system 

> 
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
04:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage LT Pro (rev dc)


With Gutsy and attached xorg.conf, I am able to get multiple monitors working. (See xorg.0.txt.gz for logs). Relevant section of xorg.conf are as 

> 
Section "Device"
        Identifier      "ati"
        Driver          "ati"
        BusID           "PCI:4:0:0"
EndSection

Section "Device"
        Identifier      "Intel"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection


Section "Monitor"
        Identifier      "IBM 6332 E74"
        Option          "DPMS"
EndSection


Section "Monitor"
        Identifier      "DELL E773s"
        Option          "DPMS"
        HorizSync       30-65
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ati"
        Monitor         "IBM 6332 E74"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "Intel"
        Monitor         "DELL E773s"
        DefaultDepth    24
        SubSection "Display"
                Depth   24
                Modes   "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen 0        "Second  Screen"  
        Screen 1        "Default Screen" RightOf "Second Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

EndSection


Now with 9.04 things don't work, i.e. I can see the output on only one monitor that is connected to Intel card. So I tried to use the working xorg.conf with 9.04. But X does not start. (See Xorg.1.txt for error logs). Relevant error messages are
> 
[    0.145477] (II) LoadModule: "ati"
[    0.146086] (II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
[    1.401002] (II) Module ati: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 6.12.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
[    1.401094] (II) LoadModule: "mach64"
[    1.401493] (II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
[    1.500193] (II) Module mach64: vendor="X.Org Foundation"
        compiled for 1.5.99.3, module version = 6.8.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0

[    1.500951] (II) MACH64: Driver for ATI Mach64 chipsets
[    1.501887] (II) Primary Device is: PCI 00@00:02:0
[    1.501950] (II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
[    1.531096] (**) MACH64(0): Depth 24, [    1.531110] (--) framebuffer bpp 32
[    1.531160] (==) MACH64(0): Using XAA acceleration architecture
[    1.531189] (WW) MACH64: Mach64 in slot 4:0:0 could not be detected!
[    1.531211] (II) UnloadModule: "mach64"
[    1.531226] (EE) Screen(s) found, but none have a usable configuration.

 

I do not see this mach64 driver being loaded in the working logs. How can I get the same (working) behaviour in 9.04.

Thanks

---

### Post by inobe on 2009-04-23
this fella has six monitors [in kubuntu 9.04]("http://www.youtube.com/watch?v=UhMErNsEoZw")


i will search the forums and try to post back with a howto :)

edit: i see you have a mach64, you must get that driver to work before anything else.

---

### Post by rnjn.sinha on 2009-04-23
Hi,

Thanks for looking into this issue. I haven't been able to figure out how this mach64 came into picture. If you see the working xorg.log (Xorg.0.txt.gz), these are the entries related to ati 
> 
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 6.7.195
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.2

(II) Loading sub module "atimisc"
(II) LoadModule: "atimisc"
(II) Loading /usr/lib/xorg/modules/drivers//atimisc_drv.so


No mention of mach64. 

One more thing, that I just noticed in lspci log for intel cards 
> 
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)


Does two occurrence imply that my 945 chipset already supports dual monitor without the need of a second card. In case yes, what type of connection cable and configuration is required?

---

### Post by inobe on 2009-04-23
you must have an ati agp card, al you have onboard intel graphics.

personally both graphics chips will give you problems, i don't think it would have anything to do with the operating system, ati needs to produce a new driver, considering amd purchased ati not so long ago they have let a lot of older cards fall out.

have a look at the mach64 driver in synaptic

---

### Post by rnjn.sinha on 2009-04-24
Just to make sure that mach64 works otherwise, I disabled the onboard Intel card (and with it lost the ability to have a dual monitor) and booted the machine. It boots up fine, although the maximum resolution that I can get is 1152x864. See the attached logs. (Xorg.0.log.gz). 
Interesting lines in this log 

> 
[    2.005749] (==) MACH64(0): Using XAA acceleration architecture
[    2.005789] (II) MACH64: Mach64 in slot 4:0:0 detected.


I again enabled the onboard Intel card and X fails to start. See the attached log (Xorg.1.log.gz). Interesting lines here are 

> 
[    1.575168] (==) MACH64(0): Using XAA acceleration architecture
[    1.575206] (WW) MACH64: Mach64 in slot 4:0:0 could not be detected!
[    1.575227] (II) UnloadModule: "mach64"
[    1.575241] (EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


However I can see that ATI card could be found in PCI probe
> 
[    0.099511] (--) PCI:*(0@0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/524288, 0xe0000000/268435456, 0xfeac0000/262144, I/O @ 0x0000e898/8
[    0.099640] (--) PCI: (0@0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/524288
[    0.144400] (--) PCI: (0@4:0:0) ATI Technologies Inc 3D Rage LT Pro rev 220, Mem @ 0xfd000000/16777216, 0xfe5ff000/4096, I/O @ 0x0000dc00/256, BIOS @ 0x????????/131072



I wonder what causes mach64 driver to not recognize the ATI card in this scenario.

---

