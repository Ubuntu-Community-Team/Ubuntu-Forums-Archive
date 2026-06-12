---
title: "Ghost monitor won't go away."
date: 2008-12-12
forum: Multimedia Software
---

### Post by SoylentBrew on 2008-12-12
My system:

Dell Optiplex 755 with an ATI Radeon HD 2400 XT running Ubuntu 8.04

When I initially set this machine up I had two smaller monitors and had a rough time getting ATI's proprietary driver working properly w/ compiz, but I eventually prevailed with lots of trial and error.

I eventually got rid of the two smaller monitors in favor of a 24" 1920x1200 display and life was good - until last night. Suddenly my machine has decided it has two monitors again and I have a 3840x1200 desktop which I cannot seem to get rid of.

I have done everything I can think of, short of sacrificing a chicken but I cannot get this thing fixed. If I stop using fglrx I can get the second monitor to go away but it won't let me go past 800x600 resolution. 

I have found plenty of advice on how to enable dual monitors and tried to apply it to removing the ghost monitor I seem to have but nothing has worked. Any advice or suggestions would be greatly appreciated.


Here is my xorg.conf:

```

Section "ServerLayout"
        Identifier     "Simple Layout"
        Screen         "Screen1" 0 0
        InputDevice    "Dell Mouse" "CorePointer"
        InputDevice    "Dell Keyboard" "CoreKeyboard"
EndSection

Section "Files"
EndSection

Section "Module"
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier  "Dell Mouse"
        Driver      "mouse"
        Option      "CorePointer"
EndSection

Section "InputDevice"
        Identifier  "Dell Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc104"
        Option      "XkbLayout" "us"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Acer"
        ModelName    "Flat Panel"
        Option      "DPMS" "true"
EndSection


Section "Device"

        # From compiz recommendations
        # vendor=1002, device=5460
        Identifier  "ATI Graphics Adapter1"
        Driver      "fglrx"
        Option      "DRI" "true"
        Option      "ColorTiling" "on"
        Option      "EnablePageFlip" "true"
        Option      "AccelMethod" "EXA"
        Option      "XAANoOffscreenPixmaps"
        Option      "RenderAccel" "true"
        Option      "AGPMode" "x"
        Option      "AGPFastWrite" "off"
        Option      "no_accel" "no"
        Option      "no_dri" "no"
        Option      "mtrr" "no"  # disable DRI mtrr mapper, driver has its own code for mtrr
        Option      "MonitorLayout" "LVDS, AUTO" #"LVDS, NONE" #"AUTO, NONE"
        Option      "IgnoreEDID" "off"
        Option      "ScreenOverlap" "0"
        Option      "NoTV" "yes"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
        Option      "CenterMode" "off"
        Option      "PseudoColorVisuals" "off"
        Option      "Stereo" "off"
        Option      "StereoSyncEnable" "1"
        Option      "FSAAEnable" "no"
        Option      "FSAAScale" "1"
        Option      "FSAADisableGamma" "no"
        Option      "FSAACustomizeMSPos" "no"
        Option      "FSAAMSPosX0" "0.000000"
        Option      "FSAAMSPosY0" "0.000000"
        Option      "FSAAMSPosX1" "0.000000"
        Option      "FSAAMSPosY1" "0.000000"
        Option      "FSAAMSPosX2" "0.000000"
        Option      "FSAAMSPosY2" "0.000000"
        Option      "FSAAMSPosX3" "0.000000"
        Option      "FSAAMSPosY3" "0.000000"
        Option      "FSAAMSPosX4" "0.000000"
        Option      "FSAAMSPosY4" "0.000000"
        Option      "FSAAMSPosX5" "0.000000"
        Option      "FSAAMSPosY5" "0.000000"
        Option      "UseFastTLS" "1"
        Option      "BlockSignalsOnLock" "on"
        Option      "UseInternalAGPGART" "no"
        Option      "ForceGenericCPU" "no"
        Option      "DesktopSetup" "horizontal" #or horizontal to stretch
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "ATI Graphics Adapter1"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
                Modes    "1920x1200"
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

```

---

### Post by gnu2tux on 2008-12-12
Can you post the output of xrandr at the command line?

Also, how many monitors does 'sudo gnome-display-properties' actually show as being set up?

I take it that you unplugged the old monitor from the graphics card and that there is only 1 monitor now actually on your PC?

Regards,

gnu2tux

---

### Post by SoylentBrew on 2008-12-12
xrandr gives:

```

X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  151 (RANDR)
  Minor opcode of failed request:  6 ()
  Serial number of failed request:  9
  Current serial number in output stream:  9

```

and 'sudo gnome-display-properties' gives me this error:

The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

I only have one monitor connected to the machine...

---

### Post by markbuntu on 2008-12-12
Did you try the detect monitors option in the Catalyst Control Center?

---

### Post by gnu2tux on 2008-12-20
sounds like your X server config is really confused.

Xrandr extension is required in Ubuntu 8.04 and up to manage your monitor.

Try ensuring that 

a) your graphics drivers are installed correctly if using an Nvidia or ATI graphics card.
b) you have no 'custom' X config in place.

to start from scratch with X, the easiest thing to do is:

$sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
$sudo dpkg-reconfigure xserver-xorg

Run through the setup and accept the specific requirements to your graphics card and monitor and then restart your system:

$sudo reboot

If still no luck, move the xorg.conf away completely so that there is literally no xorg.conf in place (8.04 and above doesn't technically need it due to Xrandr implementation) and restart gdm ( /etc/init.d/gdm stop  then /etc/init.d/gdm start)

good luck

gnu2tux

---

