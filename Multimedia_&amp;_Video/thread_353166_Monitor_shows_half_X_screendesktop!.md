---
title: "Monitor shows half X screen/desktop!"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by eztoril on 2007-02-04
Hi,

I currently have screen problems with my Kubuntu running the 2.6.19 kernel.

When starting up and the X server starts, the Nvidia splash screen is shown, but the screen is shifted approx. almost half the monitor area, showing only approx. 60% of the Nvidia logotype. Every screen after that is shown shifted in the same way (for example, the login screen and the Kubuntu desktop screen). Everything get shifted, leaving me not able to see approx. 40% of the screen/desktop!

When I installed the Kubuntu distribution the first time (Edgy), everything looked fine. The problem occured after installing a new kernel (2.6.19) and therefore was forced to reinstall the latest Nvidia driver again. The first time, I solved the problem by changing the refresh rate from 50Hz to 60Hz (or vice versa). But that trick doesn't work anymore! I can change to every refresh rate, but the problem remains. If using a 640x480x60Hz mode, problem disappears, but changing back to a higher resolution, the problem comes back (same refresh rate).
When pressing the "Auto" button on the monitor, the screen gets shifted back to normal showing the whole screen for a second, but re-syncs back to the shifted state again, showing only aprox. 60% of the screen!

My graphics card is a Nvidia GeForce 7600 GS 256MB and my monitor is a 19" HP L1925.

Can anyone help me with my problem? Please help me!

Thanks in advance!

Best regards,
   Martin

---

### Post by josesanders on 2007-02-05
Do you have multiple screens?  I've seen this on my PC with NVidia where the driver wants to output half of the display to one screen (the monitor), and the other half of the screen to a second screen (tv out, in my case).  Are you using the NVidia graphical configuration tool?  If you don't have that, I would recommend you uninstall whatever you have done, and follow this guide:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by eztoril on 2007-02-06
Thanks for the reply! I haven't tested the "Envy" script found in the link above yet, but is it compatible to my 2.6.19 kernel?

My installaton of the latest Nvidia drivers includes the "Nvidia X Server settings". Do you think the reinstall "Envy" script will fix my problem even though my monitor have shown been working with the drivers already installed?

I have tried changing many settings in this configuration window, but the result is either no difference or invalid settings (making X server not coming up again). According to the Nvidia X server settings, I cannot see that any second screen. In general, is it something I can do in the Nvidia settings window fixing my problem?

Attatched is a picture of my monitor showing the shifted screen.

Thanks in advance!

Best regards
  Martin

---

### Post by eztoril on 2007-02-09
Hi again,

Please help me! I have reinstalled the Nvidia drivers three times, two using the 'envy' script and one time using the "method 2" in the HowTo guide found almost at the end of the 'envy' homepage.

The driver installation goes fine, but my problem still remains. :( 

Again, my problem arised when I pressed the "Auto adjustment" button on the monitor. It resynced the screen leaving me being able to only view 70% of the screen.

A press on the monitor "auto adjustment" button CANNOT make any Kubuntu configuration adjustments! Therefore, my thoughts of the root cause points to the monitor, which maybe had a "default" sync setting that was fine, but it got altered when I pressed the "Auto" button and from that point in time, the monitor "remembers" the last setting (i.e. the faulty shifted setting). The question is in that case, how do I get back to the default setting?

Or does anyone have any other idea?

Very thanks in advance! Again, please help me!

Best regards,
  Martin

---

### Post by eztoril on 2007-02-11
Hi,

I have now found the 'xvidtune' program (using 'Show' button), giving me information concerning a lot of the screen parameters. These can apparently also be found in the "Monitor - modeline" section in 'xorg.conf'.

I have found out, by asking a friend, having an identical monitor, about his 'xvidtune' screen parameters. Those are:

------------------------------------------------------------------------------------------
"1280x1024"     135.00  1280  1312  1416  1664     1024  1027  1030  1064
------------------------------------------------------------------------------------------

These parameters are working for him.

I copied these settings to my 'xorg.conf' file, as shown below. This almost solved my problem. The Nvidia splash screen is now shown correctly, but within two seconds, when login screen appears, the monitor is doing an automatic adjustment showing the shifted screen back again. :( 

Also, upon Ubuntu showing the login screen shifted, I can switch the monitor between the inputs, the login screen is shown correctly for a few seconds, but again the screen gets shifted. Doing the same procedure again, gives the same result.

To me, the monitor apparently doesn't like the correct settings. What is the changes that I have to do in the 'xorg.conf' file to force the monitor to follow the screen parameters above permanently?

My xorg.conf file is found below:
-------------------------------------------------------------------------------------------------------------------------------------------
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

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

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
EndSection

Section "Files"
  
  # path to defoma fonts
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  FontPath "/usr/share/fonts/X11/misc"
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "se"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  
  # /dev/input/event
  # for USB
  Identifier "stylus"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  
  # /dev/input/event
  # for USB
  Identifier "eraser"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
  
  # /dev/input/event
  # for USB
  Identifier "cursor"
  Driver "wacom"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
  identifier "HP L1925"
  vendorname "Plug 'n' Play"
  modelname "Plug 'n' Play"
  HorizSync    30.0-82.0
  VertRefresh  56.0-76.0
  **Modeline "1280x1024"  135    1280 1312 1416 1664  1024 1027 1030 1064**
  gamma 1.0
EndSection

Section "Device"
  identifier "Nvidia GForce 7600 GS"
  boardname "NVIDIA GeForce 7 Series"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 0
  vendorname "NVIDIA"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "Nvidia GForce 7600 GS"
  Monitor "HP L1925"
  DefaultDepth 24
  option "UseFBDev" "true"
  SubSection "Display"
    depth 24
    **modes "1280x1024"**
  EndSubSection
EndSection

Section "Extensions"
  option "Composite" "Disable"
EndSection

Section "device" # 
  identifier "device1"
  boardname "NVIDIA GeForce 7 Series"
  busid "PCI:1:0:0"
  driver "nv"
  screen 1
  vendorname "NVIDIA"
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection
---------------------------------------------------------------------------------------------------------------------------------------------

Many thanks in advance!

Best regards,
   Martin

---

