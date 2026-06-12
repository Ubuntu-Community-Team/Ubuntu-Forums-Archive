---
title: "nvidia driver in X results in blank windows"
date: 2008-12-03
forum: Multimedia Software
---

### Post by rdstokes on 2008-12-03
I am trying to get my xorg.conf correct on Ubuntu 8.04.  In order to get my video to work with MythTV, I need to load the propriety "nvidia" driver.  Unfortunately, when the nvidia driver is loaded, some of my windows are completely blank.  My terminal window is blank, my "Updates are available" window is blank, and the System Monitor window is blank.  I'm sure there's more but I haven't looked around for them.

If I change the driver to "nv", then the problem doesn't occur but then I can't display video.

Below is my xorg.conf.  Can anyone tell me what is wrong with it?  Or, what questions can I answer to get me on the way?


# Xorg configuration

Section "ServerLayout"
        Identifier     "single head configuration"
        Screen      0  "Screen0" 0 0
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

#Section "Module"
#       Load  "extmod"
        #Load  "glx"
        #Load  "dbe"
        #Load  "extmod"
#EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Monitor"

 ### Comment all HorizSync and VertSync values to use DDC:
        Identifier   "Projector"
        VendorName   "Optima"
        ModelName    "Optima EP1690"
 ### Comment all HorizSync and VertSync values to use DDC:
        VertRefresh  60.0 - 60.0
EndSection

Section "Device"
        Identifier  "Card0"
        Driver      "nv"
        VendorName  "nVidia Corporation"
        BoardName   "NV34 [GeForce FX 5200]"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Projector"
        DefaultDepth     16
EndSection





Rob
My configuration is: 
MythTV version: 0.21.20080304-1 16838
Ubuntu 8.04.1, kernel version: 2.6.24-21-generic
CPU: Intel Pentium 4 CPU 3.2GHz Socket 775 800 FSB w/Hyper Threading Technology 
Memory: 1Gig DDR 333 Memory 180 Pin 
Motherboard: ASRock 775i65G Mother Board 
Optical Drive: LG 18X DVD RW + Dual Layer 
Hard Drive: 1 Western Digital 1 TB 7200 RPM Cache Serial ATA
Video onboard: Integrated SiS Ultra256 2D/3D Graphics 
Video card: Micro-star International (MSI) AGP GeForce FX5200-TD128LF, 8X, 128M, DDR1, D-Sub, DVI-D, TV-out
Audio onboard: AUDIO ADI AD1888 6-channel audio CODEC 
Audio card: Riviera C-Media CMI 8738 (Connected to my entertainment center via the optical cable)
Network Card: Onboard 10/100 Network Card 
Tuner card: 2 pcHDTV HD-5500

---

