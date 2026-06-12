---
title: "fglrx problems with ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
date: 2006-08-18
forum: Multimedia &amp; Video
---

### Post by Xtreme it on 2006-08-18
I've upgraded from 5.10 to 6.06 and my ATI 3D acceleration stop working.
 
I think I've read all the post about this issue, and tried all proposals of solution found, but I keep getitng "MESA" on fglrxinfo:
```

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

A few things about the actual status:
```

$ lspci -n |grep 0300
0000:01:00.0 0300: 1002:4e50

```

```

$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

```

```

$ cat /etc/X11/xorg.conf

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen         "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pt+inet(tsu1557)"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Driver          "fglrx"
        VideoRam        65536
#       Option          "UseInternalAGPGART" "no"
#       Option          "VideoOverlay"  "on"
#       Option          "OpenGLOverlay" "off"
#       Option          "PseudoColorVisuals"    "off"
        Screen          0
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30.0 - 67.0
        VertRefresh  50.0 - 75.0
        Option      "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

```

```

$ lsmod
Module                  Size  Used by
(...)
intel_agp              22940  1
agpgart                34888  2 fglrx,intel_agp
(...)

```

With glxgears I can hardly see them moving on the screen.
```

$ glxgears -printfps
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
601 frames in 5.5 seconds = 108.929 FPS
684 frames in 5.8 seconds = 118.888 FPS

```

I see my computer is a lot similar to mathew's ([http://www.geocities.com/ubuntumatthew/aopen1557gls.html]("http://www.geocities.com/ubuntumatthew/aopen1557gls.html")) but with a 64Mb Graphics card and a 1.7GHz processor.

Can anyone give me some help here?

Other problem not solved yet is that I cannot play any video file anymore (didn't spent any time on this issue though).

---

### Post by Xtreme it on 2006-08-18
Follows my dmeg and Xorg.0.log outputs:

```

$ dmesg
[17179569.184000] Linux version 2.6.15-26-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Aug 3 02:52:00 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000d8000 - 00000000000e0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003ff70000 (usable)
[17179569.184000]  BIOS-e820: 000000003ff70000 - 000000003ff7b000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003ff7b000 - 000000003ff80000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003ff80000 - 0000000040000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffff000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262000
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32624 pages, LIFO batch:7
[17179569.184000] DMI present.
(...)
[17179598.676000] Linux agpgart interface v0.101 (c) Dave Jones
[17179598.680000] agpgart: Detected an Intel 855PM Chipset.
[17179598.696000] agpgart: AGP aperture is 256M @ 0xe0000000
(...)
[17179602.620000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179602.624000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179602.624000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0
(...)
[17179620.144000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179620.148000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179620.148000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179620.148000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179620.148000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179620.148000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179620.148000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179620.156000] [fglrx] total      GART = 268435456
[17179620.156000] [fglrx] free       GART = 252440576
[17179620.160000] [fglrx] max single GART = 252440576
[17179620.160000] [fglrx] total      LFB  = 59060224
[17179620.160000] [fglrx] free       LFB  = 47165440
[17179620.160000] [fglrx] max single LFB  = 47165440
[17179620.160000] [fglrx] total      Inv  = 0
[17179620.160000] [fglrx] free       Inv  = 0
[17179620.160000] [fglrx] max single Inv  = 0
[17179620.160000] [fglrx] total      TIM  = 0
(...)

```

As this output is too long I've attached a file with it.

---

### Post by matthew on 2006-08-20
Try this:

1. Install or re-install the linux-restricted-modules for your kernel
(eg. if you are using linux-image-386, then install linux-restricted-modules-386)

2. Install or re-install xorg-driver-fglrx.

3. Run the command ```
sudo dpkg-reconfigure xserver-xorg
```which will start a menu driven configuration process. Select the fglrx driver when you have the chance. You can also set the color depth (I recommend 24 bit) and the display resolution you want during the process. For everything else the default choices should work for you.

4. Reboot and all ***should*** work. You can confirm using the steps you tried earlier, fglrxinfo and glxgears.



You may want to install the fglrx-control package as well. It gives you a nifty control panel that you can run from the terminal with the command ```
fireglcontrolpanel
```

---

### Post by Xtreme it on 2006-08-20
Although not confident on the results I tried your proposed approach reinstalling linux-restricted-modules-386 and xorg-driver-fglrx packages.

(I think the reinstalling the first one does nothing as it is only a "ghost" of the restricted modules of the current kernel version.)

reconfiguring the xserver-xorg changed my /etc/X11/xorg.conf file, although the changes where not much, the new contents follow:

```

$ cat /etc/X11/xorg.conf
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
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pt+inet(tsu1557)"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        VideoRam        65536
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-67
        VertRefresh     50-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x768" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x768" "1024x768" "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

As for the rest... 

no changes neither in fglrxinfo or glxgears. I get the same results as before.

Any more options?

---

### Post by matthew on 2006-08-20
Hmm...that was all I had to do. 

Here's another idea to try...take a look at this as it has a couple of steps in addition to what I gave. I suggest starting at the beginning and going through all of them again even though you have done many of them before.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-5ead174a0b3294527486cd4d71ded66b40003f25)

---

### Post by Xtreme it on 2006-08-22
](*,)  Well, I'm out of options... should I quit?

After reading the post about the issue (even for other flavors of Linux):

[LIST]
[*]reinstalling the proposed pakages
[/LIST]
```

sudo apt-get install --reinstall linux-restricted-modules-386
sudo apt-get install --reinstall xorg-driver-fglrx
sudo apt-get install --reinstall libstdc++5 

```

[LIST]
[*]recreating all configuration steps, as the use of...
[/LIST]
```

sudo dpkg-reconfigure xserver-xorg
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

[LIST]
[*]blacklist modules in /etc/modprobe.d/blacklist
[/LIST]
```

blacklist agpgart
blacklist intel_agp

``` 

[LIST]
[*]Editing the "Device" section of /etc/X11/xorg.conf
[/LIST]
```

    Option "UseInternalAGPGART" "no"

```

...Of course I made several atempts with diferent configs but I always got the same results... No Ati driver, only Mesa!

The current status if the following:

```

$ cat /etc/X11/xorg.conf
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen  0       "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pt+inet(tsu1557)"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Driver          "fglrx"
        VideoRam        65536
#       Option          "UseInternalAGPGART" "no"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
#       Option          "PseudoColorVisuals"    "off"
        Screen          0
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30.0 - 67.0
        VertRefresh  50.0 - 75.0
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection

```

```

$ dmesg |grep fglrx
[17179610.236000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179610.240000] [fglrx] Maximum main memory to use for locked dma buffers: 929 MBytes.
[17179610.240000] [fglrx] module loaded - fglrx 8.25.18 [May 18 2006] on minor 0[17179630.056000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[17179630.056000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[17179630.056000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of chipset)
[17179630.056000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[17179630.064000] [fglrx] total      GART = 268435456
[17179630.064000] [fglrx] free       GART = 252440576
[17179630.064000] [fglrx] max single GART = 252440576
[17179630.068000] [fglrx] total      LFB  = 59060224
[17179630.068000] [fglrx] free       LFB  = 47165440
[17179630.068000] [fglrx] max single LFB  = 47165440
[17179630.068000] [fglrx] total      Inv  = 0
[17179630.068000] [fglrx] free       Inv  = 0
[17179630.068000] [fglrx] max single Inv  = 0
[17179630.068000] [fglrx] total      TIM  = 0

```

```

$ lsmod |grep fglrx
fglrx                 388908  8
agpgart                34888  2 fglrx,intel_agp

```

```

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

```

$ fgl_glxgears
Using GLX_SGIX_pbuffer
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  33
  Current serial number in output stream:  33

```

My Xorg.0.log goes attached.

Help really needed here!

---

### Post by Xtreme it on 2006-08-24
**SOLVED**=D> :lol: =D>**SOLVED**

After reading [this other post]("http://www.ubuntuforums.org/showthread.php?t=197471&highlight=mobility+radeon") I decided not to give up and give it another try.

I did (almost) all the steps (I did cheated a little), and it did not work! and I was ](*,) once again. but it made me look closelly at the output of glxinfo (unfortanelly I don't have a copy of it), and I noticed an error here with /usr/X11R6/lib/modules/dri/fglrx_dri.so not being found (it is in /usr/lib/dri/).

Then I created a symlink to it:
```

sudo ln -s /usr/X11R6/lib/modules/dri /usr/lib/dri/

```

Rebooted and... Mesa again!
Checked again the output of glxinfo and got a diferrent error with fglrx_dri.so again but this time something with _glapi_add_entrypoint2 not being supported (remember that at the time I had the libGL.so.1.2 from ATI driver version 8.24.8).

I decided then to rollback the actions undertaken from the previous link (restoring thus the default configuration), with exception of the xorg.conf file.

Rebooted and... "voila"! =D> It works now.

```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
```

```
$ fgl_glxgears
Using GLX_SGIX_pbuffer
1990 frames in 5.0 seconds = 398.000 FPS
2176 frames in 5.0 seconds = 435.200 FPS
2089 frames in 5.0 seconds = 417.800 FPS
```

```
$ glxgears -printfps
10804 frames in 5.0 seconds = 2160.354 FPS
10922 frames in 5.0 seconds = 2184.360 FPS
10902 frames in 5.0 seconds = 2180.290 FPS
```

```
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_hyperpipe, GLX_SGIX_swap_barrier,
    GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9600 Generic
OpenGL version string: 2.0.5814 (8.25.18)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array,
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters,
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100,
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp,
    GL_ARB_texture_compression, GL_ARB_texture_cube_map,
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine,
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3,
    GL_ARB_texture_mirrored_repeat, GL_ARB_transpose_matrix,
    GL_ARB_vertex_blend, GL_ARB_vertex_buffer_object, GL_ARB_vertex_program,
    GL_ARB_vertex_shader, GL_ARB_window_pos, GL_ARB_draw_buffers,
    GL_ATI_draw_buffers, GL_ATI_element_array, GL_ATI_envmap_bumpmap,
    GL_ATI_fragment_shader, GL_ATI_map_object_buffer, GL_ATI_separate_stencil,
    GL_ATI_texture_env_combine3, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_ATI_vertex_array_object,
    GL_ATI_vertex_attrib_array_object, GL_ATI_vertex_streams,
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route,
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra,
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax,
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint,
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap,
    GL_EXT_texgen_reflection, GL_EXT_texture3D,
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine,
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic,
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp,
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array,
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square,
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix,
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  1 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  1 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  2 1 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  2 1 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  4 1 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  4 1 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  1 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  1 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  6 1 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  6 1 None
```

```
$ cat /etc/X11/xorg.conf
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen  0       "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "pt+inet(tsu1557)"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Driver          "fglrx"
        VideoRam        65536
        Option          "UseInternalAGPGART" "no"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Screen          0
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier   "Generic Monitor"
        HorizSync    30.0 - 67.0
        VertRefresh  50.0 - 75.0
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" "1280x1024" "1152x864" "1024x768" "800x600"
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection
```

Sumary: The problem was only the fact that the file fglrx_dri.so was being searched in the wrong place. Thus a better attention to glxinfo command output would avoid a lot of time being spent on this issue. 

One last word to mathew to thank his help on this issue.

---

