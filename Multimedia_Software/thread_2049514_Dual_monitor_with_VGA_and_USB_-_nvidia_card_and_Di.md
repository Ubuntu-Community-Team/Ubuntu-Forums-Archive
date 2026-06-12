---
title: "Dual monitor with VGA and USB - nvidia card and DisplayLink"
date: 2012-08-28
forum: Multimedia Software
---

### Post by muniubun on 2012-08-28
I am trying to get a dual monitor set up is working on Ubuntu 11.10. The main screen is fine, the second (right) is white. The mouse moves the cursor correctly across the screens, but nothing but white is on the right. I also cannot drag a window from the left to the right.

If I click on the white monitor, I lose all the icons from the working monitor and the right screen changes from white to the default desktop as used on the main monitor.

I have a Next-Generation NVIDIA ION graphics with 512MB DDR3 VRAM card&#8232;Ubuntu 11.10 32 bit (but will be glad to upgrade or downgrade to make it work)&#8232;NVIDIA driver version 280.13

The main monitor is a Lilliput 10.1" Um-1010/c USB Monitor (Non-touch Screen) By Viviteq Inc

I have not been able to make the iEi AFL-12M VGA monitor to work as main that is why the USB is main.

The output of:

sudo lshw -C display; lsb_release -a; uname -a; dpkg -l | grep nvidia

is:

```

*-display              
       description: VGA compatible controller
       product: GT218 [ION]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:19 memory:fa000000-faffffff memory:d0000000-dfffffff memory:ce000000-cfffffff ioport:dc00(size=128) memory:fbd00000-fbd7ffff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.10
Release:    11.10
Codename:    oneiric
Linux deeporange-ivi 3.0.0-24-generic #40-Ubuntu SMP Tue Jul 24 15:36:59 UTC 2012 i686 i686 i386 GNU/Linux
ii  nvidia-common                          1:0.2.35                                Find obsolete NVIDIA drivers
ii  nvidia-current                         280.13-0ubuntu6.2                       NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        280.13-0ubuntu2                         Tool of configuring the NVIDIA graphics driver

```Thanks in advance for your help.

---

### Post by muniubun on 2012-08-29
This is the xorg.conf file I am using:

> 
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "DisplayLinkScreen" 0 0
    ### Changed Screen1 to DisplayScreen    
    Screen      1  "Screen0" RightOf "DisplayLinkScreen"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option          "Xinerama" "off"
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
    Load  "glx"
    Load  "dri2"
    Load  "dri"
    Load  "dbe"
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
    Identifier   "Monitor0"
    DisplaySize  245 184
EndSection

Section "Monitor"
    Identifier  "DisplayLinkMonitor"
    DisplaySize  202 114
EndSection

Section "Device"
    Identifier  "DisplayLinkDevice"
    Driver      "displaylink"
    Option      "fbdev" "/dev/fb0"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "nvidia"
        Option      "fbdev" "/dev/fb1"
EndSection

Section "Screen"
    Identifier  "DisplayLinkScreen"
    Device      "DisplayLinkDevice"
    Monitor     "DisplayLinkMonitor"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    ### From nvidia configuration
    #Option     "fbdev" "/dev/fb1"
    #SubSection "Display"
    #    Modes   "nvidia-auto-select"
    #EndSubSection
EndSection



---

