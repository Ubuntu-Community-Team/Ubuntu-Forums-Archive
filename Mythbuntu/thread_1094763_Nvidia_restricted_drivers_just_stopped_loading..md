---
title: "Nvidia restricted drivers just stopped loading."
date: 2009-03-12
forum: Mythbuntu
---

### Post by Hackit on 2009-03-12
Oh No, I'm almost there.

I have been putting so much time into this system I can't believe I just lost my nvidia drivers.

Here's what has happened, I rebooted and get this message we are unable to loag xconfig, running in low graphics mode.

Well I've been using the 1.77 driver and have an nvidia 8600 gts card.

I load up the nvidia control panel and get this message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
---------------------------------------------------------------
So i ran this is terminal:

hackit@MYTH-HTPC:~$ sudo nvidia-xconfig
[sudo] password for hackit: 

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: No Layout specified, constructing implicit layout section using
         screen "Default Screen".


WARNING: Unable to find CorePointer in X configuration; attempting to add
         new CorePointer section.


WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: Unable to find CoreKeyboard in X configuration; attempting to add
         new CoreKeyboard section.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
-------------------------------------------------------------

Not sure what i'm supposed to do?

So i ran this in terminal - sudo gedit /etc/X11/xorg.conf.


And this is what the xorg file says:

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection
-------------------------------------------------------

How can i modify this file and know what my settings should be?

Thanks for any help.

---

### Post by nickrout on 2009-03-12
Now restart X. Three ways:

[LIST=1]
[*]ctrl-alt-backspace (kills X which should automatically restart); or
[*]sudo /etc/init.d/gdm restart (restarts the X display manager which will kill X and restart it); or
[*]restart the computer
[/LIST]

---

