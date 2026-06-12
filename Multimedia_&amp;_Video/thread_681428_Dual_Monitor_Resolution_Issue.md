---
title: "Dual Monitor Resolution Issue"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by Reverence15498 on 2008-01-28
I have just recently begun using dual monitors on my Geforce 6600 and am having a resolution problem.  I Have both monitors displaying twinview like I want but my 2nd screen resolution won't go any higher than 640x480 without making it so I have to scroll around the screen even though the monitor is built to go up to 1600x1200. It is a Compaq FS940. To set up the dual mode I used the Nvidia X server program installed with envy. I have also tried using the "screen and graphics" tab with no success. I was wondering if there was another way I might try to get my 2nd screen to perform at the resolution that it is capable of. 

Thanks in advance!

---

### Post by overdrank on 2008-01-29
> **Reverence15498 said:**
> I have just recently begun using dual monitors on my Geforce 6600 and am having a resolution problem.  I Have both monitors displaying twinview like I want but my 2nd screen resolution won't go any higher than 640x480 without making it so I have to scroll around the screen even though the monitor is built to go up to 1600x1200. It is a Compaq FS940. To set up the dual mode I used the Nvidia X server program installed with envy. I have also tried using the "screen and graphics" tab with no success. I was wondering if there was another way I might try to get my 2nd screen to perform at the resolution that it is capable of. 

Thanks in advance!

HI and welcome, I had a similar issue with my son's system and I had to uninstall the drivers reboot then install them again. It may help and good luck!

---

### Post by Reverence15498 on 2008-02-02
Thanks for the tip. I have recently tried reinstalling to no avail. I have also tried editing my xorg.conf file but it  just boots up the computer and gives me a msg about wanting to run in low resolution mode. any other suggestions?

---

### Post by Pgi947 on 2008-03-22
Getting the exact same issue, installed restricted Nvidia  drivers that came with ubuntu 7.10, sets  my HDTV (DVI) to 1368x768 (its native max) but will only set my PC monitor to a max of 640x480 59hz, while it is capable of displaying upto 1400x900 80hz.

I've tried just about everything I can think of, wipe, reinstall, re-configure xorg.conf, editing xorg.conf, recompiling xorg.conf.

Everything I try results in the monitor becoming 'disconnected' as it thinks it can't display above 640x480 and have to reset the monitor to 480p to get anything.

Also in ubuntus native resolution options, I'm given one resolution only, and it claims  there is only 1 monitor connected and running when there is blatently two...

Even if running seperate X for 2 monitors still only get a max resolution on my '2nd' monitor of 480p

anyone any ideas at all? I'll try anything (within reason lol) to get this to run flawlessly :-)

---

### Post by Greasy on 2008-03-22
Try choosing the correct monitor in System>Administration>Screen & Graphics options.

---

### Post by Pgi947 on 2008-03-22
Sorry forgot to mention, Ubuntu also shows me as using only 1 monitor in the screen and graphics option, and ONLY 1 resolution, which is a combined resolution of the 1368x768 and 640x480 something along the lines of 2008x288 or something messed up...

---

### Post by Larissa on 2008-03-22
It's ATI in my case, but maybe it helps for you to know that there seems to be a problem when loading the fglrx twice -> I have two graphics cards in the PC for which both I wanted to load the fglrx; one would fail and the screen resolution would be very very low.

Also I recognized on my notebook (NVIDIA graphics card) if I connect via VGA instead of DVI sometimes it's only found the be a "CRT" (no brand read out) making it impossible to increase the resoltion to more than 640x480. Maybe this applies rather than the suggestion above.

Does someone have an idea why this is?

---

### Post by Pgi947 on 2008-03-22
That sounds very fermilliar Larissa.

Secondry monitor, connected via VGA, just reports as CRT:0 with the highest usable resolution set to 640x480.

Is there any possible way we can change the values of CRT:0 to for instance another DFP? this should in theory give us the much needed higher resolutions?

---

### Post by Larissa on 2008-03-22
Theory should grant you the full though it's VGA. Just an idea: Do you connect via a docking station?

---

### Post by Pgi947 on 2008-03-22
No connected directly to the GPU, monitor only has VGA input also, so I really need a solution for this :-)

I'm going to tweak around with some xorg.conf settings again I think, try completely clone all the settings from the DVI monitor to the VGA monitor and see if that gives me the extra set of values needed :-)

In the mean time, any more ideas keep them comming....

---

### Post by Larissa on 2008-03-22
> **Pgi947 said:**
> In the mean time, any more ideas keep them comming....
Sometimes it would help restarting the X-Server after connecting (Ctrl+Alt+Backspace)

---

### Post by Pgi947 on 2008-03-22
Tried restarting the X server after ever configuration tweak applied... would near always result in the 2nd monitor becomming 'disconnected' thus requiring me to re-set the settings back to 640x480 to get any display on monitor 2.

---

### Post by Larissa on 2008-03-22
Do you have the latest driver applied? Maybe try [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to do so.

---

### Post by Pgi947 on 2008-03-22
I'll try the envy install later this evening see if it makes any changes :-)

---

### Post by Pgi947 on 2008-03-25
Ok tried envy, same issue, tried manual install of the nvidia driver from a non GUI terminal, installed fine, same problem, highest resolution on 'CRT:0' is still 640x480...

Any more suggestions people?

---

### Post by overdrank on 2008-03-25
> **Pgi947 said:**
> Ok tried envy, same issue, tried manual install of the nvidia driver from a non GUI terminal, installed fine, same problem, highest resolution on 'CRT:0' is still 640x480...

Any more suggestions people?

HI and please post your xorg ```
cat /etc/X11/xorg.conf
```
You can use the code tags in the message box to conserve space. #

---

### Post by gdrumm on 2008-03-25
Same kind of issue here.
I'm running a Dell D620 laptop, through a Dell docking station that uses the Nvidia driver, connected to a Dell 19" LCD monitor.  I can only get 640x480 no matter what I do.

I currently have the laptop docked and closed, so that I'm only using the 19", and I still get 640x480.

Boot screen resolution shows fine, I think it's at least 800x600, but I'm not sure.  As soon as it boots, it goes back to the 640x480 resolution.

Argh!

---

### Post by Pgi947 on 2008-03-27
xorg.conf, withe both monitors enabled

> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:21:33 PST 2008

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-1"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8500 GT]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8500 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8500 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT: nvidia-auto-select +1368+0, DFP: nvidia-auto-select +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


---

