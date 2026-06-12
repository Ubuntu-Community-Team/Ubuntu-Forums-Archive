---
title: "ATI X1650 fglrx problems"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by niobos on 2007-10-28
Hi,

I'm a total newbie to (k)ubuntu, but I do have experience with Gentoo, so I know how to handle the bash-prompt and stuff.

I do realize that this question is probably asked a hundred times before, but I couldn't find a matching "symptoms-section", so here I go:

I have an ATI/AMD X1650 AGP card with ASUS branding (AX1650PRO) with 2 monitors connected (19"TFT on the DVI, 19" CRT on the VGA). My goal is to get Compiz running in a big-desktop-like setup, but currently I can't even get X started in single-screen.

I downloaded the latest ATI-drivers and installed them using this guide: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
I didn't find a section for Kubuntu 7.10, but I followed the Ubuntu 7.04 steps. (was this a good idea?)

When I boot Kubuntu, I get the usual framebuffer-splash-thing. Then the splash disappears and X.org should start, but all I get is a black screen and a complete lockup. CTRL-ALT-Backspace, CTRL-ALT-Del, ACPI-power-button: none of them give any response at all.

So I retried to start X, but from recovery-mode and captured the output (via serial line): 
```
<snip>

* Loading hardware drivers...        
[  118.584660] Linux agpgart interface v0.102 (c) Dave Jones
[  118.808519] agpgart: Detected an Intel 865 Chipset.
[  118.875751] agpgart: AGP aperture is 256M @ 0xd0000000

<snip>

[  120.626287] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  120.776958] [fglrx] Maximum main memory to use for locked dma buffers: 1414 MBytes.
[  120.868568] [fglrx] ASYNCIO init succeed!
[  120.916759] [fglrx] PAT is enabled successfully!
[  120.972017] [fglrx] module loaded - fglrx 8.42.3 [Oct 19 2007] on minor 0

<snip>

root@XXXXXXXX:~# startx
xauth:  creating new authority file /root/.serverauth.5017

X: warning; process set to priority -1 instead of requested priority 0

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux XXXXXXXX 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 28 09:28:56 2007
(==) Using config file: "/etc/X11/xorg.conf"
(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(II) Module already built-in
(II) Module already built-in
(EE) fglrx(0): Failed to enable interrupts.
[atiddx] ASYNCIO init succeed!

<complete lockup here>
```
I only pasted the interesting lines (or rather: the lines I thought were interesting). I have the complete serial dump (from kernel bootup to lockup), so if you need more, please ask.

My xorg.conf (relevant parts, but again, please ask if you need more):
```

Section "Device"
        Identifier      "ATI Technologies Inc ATI Default Card"
        Driver          "fglrx"
        Busid           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc ATI Default Card"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1280x960"      "1152x864"      "1024x768"      "832x624"       "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection

```

I should add that I have this card working in Gentoo and fglrx (8.37.6) in a big-desktop setup with 3D acceleration. (but without compiz)

---

### Post by kondyj on 2007-10-29
Hi,

I got this working.

Backup your (not working) xorg.conf file. 

Download the latest ATI drivers (26. Oct).

1) Restricted drivers -> disable ATI accelerated graphics driver

2)
sudo apt-get remove xserver-xgl
sudo apt-get remove xorg-driver-fglrx

3)
reboot

You should be able to start X with vesa drivers now.

Install the ATI drivers : sudo ./ati-driver-installer-8.42.3-x86.x86_64.run

I even did the automatic option.

Reboot

If modules dont load for some reason :

 sudo insmod /lib/modules/2.6.22-14-generic/misc/fglrx.ko 
 or sudo modprobe fglrx

My current xorg.conf (im not done with this yet, its a cut&paste job from a bunch of how-to's) :

```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "stylus" "SendCoreEvents"
        InputDevice    "cursor" "SendCoreEvents"
        InputDevice    "eraser" "SendCoreEvents"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "dri"
        Load  "v4l"
        Load  "dbe"
        Load  "glx"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
        Option      "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "stylus"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "stylus"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "eraser"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "eraser"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
        Identifier  "cursor"
        Driver      "wacom"
        Option      "Device" "/dev/wacom"          # Change to 
        Option      "Type" "cursor"
        Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "HSync2" "30-81" #This sets the horizontal sync for the secondary display. 
        Option      "VRefresh2" "56-76" #This sets the refresh rate of the secondary display.
        Option      "DesktopSetup" "horizontal"
        Option      "Mode2" "1280x1024"
        Option      "MonitorLayout" "LVDS,LVDS"
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Virtual   1280 1024
                Viewport  0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

When you start X next time, open up a terminal and type :

```
SKIP_CHECKS=yes compiz
```

And you should have this : [http://www.youtube.com/watch?v=oyoNCqwZX38](http://www.youtube.com/watch?v=oyoNCqwZX38)

```

desktop:~$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6958 Release

```

---

### Post by niobos on 2007-10-29
I retried with an (almost) copy of your xorg.conf, but get the same result: total lockup as soon as X starts. I also tried to remove every single option from the driver-section, leaving a plaint fglrx-driver; same result: total lockup.
I didn't even get around to install compiz yet, just trying to get Xorg to work with fglrx 8.42.3...

---

### Post by kondyj on 2007-10-29
Hi,

Gimme output from :

lsmod | grep fgl

and

fglrxinfo

---

### Post by niobos on 2007-10-29
Let me first add: 8.37.6 works as it should (but, off course, without AIGLX and compiz and eye-candy).
8.42.3 also locks up gentoo just like Ubuntu, so it's definitely not Ubuntu's fault.

As a reference, from my working gentoo setup (same machine, different partition, 8.37.6):
lsmod (trimmed) ```

Module                  Size  Used by
fglrx                 645152  15
agpgart                24780  2 fglrx,intel_agp

```
glxinfo```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe,
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample,
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6473 (8.37.6)

<snip>
```

Now from the non-working ubuntu setup (8.42.3)
lsmod (grep-ed)```

Module                  Size  Used by
fglrx                1487340  0
agpgart                35016  2 fglrx,intel_agp

```
fglrxinfo failed: Error: unable to open display :0

---

### Post by kondyj on 2007-10-29
Ok, you are using the old version on gentoo and new on ubuntu...then let me have this :

cat /var/log/Xorg.0.log | grep EE
cat /var/log/Xorg.0.log | grep WW

...and gimme output from :

lshw

as well (the video stuff)

and your Device section from xorg.conf

(my fglrxinfo give me this :

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6958 Release

)

---

### Post by niobos on 2007-10-30
> **kondyj said:**
> Ok, you are using the old version on gentoo and new on ubuntu...
Yes, but I also tried the reverse (8.37.6 on ubuntu, 8.42.3 on gentoo) and the problem is driver-related, not distro-related: i.e. gentoo+8.42.3 crashed just the same, ubuntu+8.37.6 works fine.

As stated in my first post: X doesn't start. The machine locks up before I get any graphics on the screen. But I think the graphic-mode is switched to 1280x1024, since my CRT gives his usual tick. Xorg.0.log isn't created, since he locks up before he can write it. startx gives some output (see first post)

lshw (stripped to what I think is interesting, let me know if I'm wrong)
```

    description: Desktop Computer
    product: MS-7012
    vendor: MEDIONPC
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop
  *-core
       description: Motherboard
       product: MS-7012
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: 6.00 PG (02/24/2004)
          size: 128KB
          capacity: 192KB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot
     *-pci
          description: Host bridge
          product: 82865G/PE/P DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-pci:0
             description: PCI bridge
             product: 82865G/PE/P PCI to AGP Controller
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 9e
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 msi vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: ATI Technologies Inc
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 9e
                width: 32 bits
                clock: 66MHz
                capabilities: pm cap_list
                configuration: latency=32 mingnt=8

```

parts of my xorg.conf (which crashes)
```

Section "dri"
    Mode 0666
EndSection

Section "Module"
    Load        "dbe"   # Double buffer extension
    # This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a
    Load        "v4l"
EndSection

Section "Files"
    # <snip>
EndSection

Section "InputDevice"
    Identifier  "Keyboard1"
    # <snip>
EndSection

Section "InputDevice"
    Identifier  "Mouse1"
    # <snip>
EndSection

Section "Monitor"
    Identifier  "Iiyama"
    HorizSync   30-150
    VertRefresh 50-200
    Option "DPMS"
EndSection

Section "Monitor"
    Identifier  "Samsung SyncMaster 930BF"
    HorizSync   30-65 #30-81
    VertRefresh 56-75
    Option "DPMS"
EndSection

Section "Device"
    Identifier                          "ATI-0"
    Driver                              "fglrx"
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI-0"
    Monitor     "Samsung SyncMaster 930BF"
    DefaultDepth 24

    Subsection "Display"
        Depth       24
        Modes       "1280x1024" "1024x768" "800x600" "640x480"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "Server Layout"
    Screen 0 "Screen0"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection

```

---

### Post by kondyj on 2007-10-31
Ok..i think you should go back to basic..and just try to get this up with one monitor with the new fglrx driver.

Just one question first..do you get X running if you start failsafe or with vesa drivers?

Try this in your xorg.conf file :

Remove the second monitor (i assume the syncmaster) and add this :

Section "Monitor"
    Identifier  "Iiyama"
    HorizSync   30-150
    VertRefresh 50-200
    **Option "DPMS" "true"**
EndSection

Try adding this :

Section "Device"
    Identifier                          "ATI-0"
    Driver                              "fglrx"
    BusID                               "PCI:1:0:0"
EndSection

Do not load any modules, just leave it empty or remove the entire section.

**Remove the Extension composite stuff if you have that. Also remove the dri/0666 section.**

Add this screen: 

Section "Screen"
        Identifier      "testscreen"
        Device          "ATI-0"
        Monitor         "Iiyama"
        DefaultDepth    16
        SubSection "Display"
                Depth   16
                Modes   "800x600"
        EndSubSection
EndSection

And this Serverlayout :

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "testscreen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Here is my lshw :

```

        *-pci:0
             description: PCI bridge
             product: 82945G/GZ/P/PL PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-display:0
                description: VGA compatible controller
                product: RV530LE [Radeon X1600/X1650 PRO]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=0 module=fglrx
           *-display:1 UNCLAIMED
                description: Display controller
                product: RV530LE [Radeon X1650 PRO] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@0000:01:00.1
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=0


```

---

### Post by niobos on 2007-11-01
> **kondyj said:**
> Ok..i think you should go back to basic..and just try to get this up with one monitor with the new fglrx driver.That would be a nice start, indeed.
> **kondyj said:**
> Just one question first..do you get X running if you start failsafe or with vesa drivers?It works with VESA as well as the old 8.37.6 fglrx.

The new xorg.conf:```

Section "Module"
    # <all comments>
EndSection

Section "Files"
    # <font path listing>
EndSection

Section "InputDevice"
    Identifier  "Keyboard1"
    # <same as previous>
EndSection

Section "InputDevice"
    Identifier  "Mouse1"
    # < same as previous>
EndSection

Section "Monitor"
    Identifier  "Iiyama"
    # <still in but unused>
EndSection

Section "Monitor"
    Identifier  "Samsung SyncMaster 930BF"
    HorizSync   30-65 #30-81
    VertRefresh 56-75
    Option "DPMS" "true"
EndSection

Section "Device"
    Identifier                          "ATI-0"
    Driver                              "fglrx"
    BusID           "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier  "Screen0"
    Device      "ATI-0"
    Monitor     "Samsung SyncMaster 930BF"
    DefaultDepth 16

    Subsection "Display"
        Depth       16
        Modes       "800x600"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier  "Server Layout"
    Screen 0 "Screen0"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"
EndSection
```
This gives the same observable result: black screen and non-responsive to CTRL-ALT-Backspace and CTRL-ALT-DEL and ACPI-power-button. (but, off course, my second screen loses video sync and goes to sleep)

I'm getting a little desperate on this video card.....:(
I really do appreciate all your help!

---

