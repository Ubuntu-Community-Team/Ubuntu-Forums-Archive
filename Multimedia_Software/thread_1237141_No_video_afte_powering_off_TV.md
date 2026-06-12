---
title: "No video afte powering off TV"
date: 2009-08-11
forum: Multimedia Software
---

### Post by danbaatar on 2009-08-11
I just bought a Vizio VL370M TV that I have hooked up to my computer with a DVI to HDMI adapter.  I have an nVidia graphics card (shows up as GeForce 7300 GS in lspci) with the proprietary nVidia driver installed under Jaunty.

If I have my TV on and set to the right input, then everything works out OK.  The display comes up and works just fine.  I can change inputs on the TV and come back to the computer input and everything is still OK.

If I turn off the TV, though, I can't get the image to come back.  At first it gives the message "retrieving information", and then either "No signal!" or "Not support!" on a blue screen.  Occasionally, I'll get a flash of a highly distorted version of the image that is supposed to be on the screen, with random horizontal lines.

I've tried just restarting the X-server by typing "/etc/init.d/gdm restart".  That doesn't work, although if I reboot the computer, everything comes back up just fine again.

Does anyone have an idea of what might be going on here?  I'd really appreciate the help.  Here's my xorg.conf file:

```
Section "ServerLayout"

# commented out by update-manager, HAL is now used
#    InputDevice    "Keyboard0" "CoreKeyboard"
# commented out by update-manager, HAL is now used
#    InputDevice    "Mouse0" "CorePointer"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "VIZ VL370M"
    HorizSync       31.0 - 70.0
    VertRefresh     50.0 - 77.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
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

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by danbaatar on 2009-08-13
I found out something else that may be useful.  One of the things I use the computer for is as a Myth box.  If the Myth menu is up when I hit the power button on the TV, in the instant before the TV actually goes blank, there is some activity on the menu, almost as if I had pushed "exit" on my remote.

Could the TV be sending some signal to the graphics card that causes it to enter some sort of power-saving state that it isn't able to wake up from when I turn the TV back on?

---

### Post by markbuntu on 2009-08-13
The tv is telling the graphics card goodbye. 

It is a problem with some graphics drivers that they are unable to handle "hot plugging". In other words they work fine if everything is plugged in when they start up but they have trouble dealing with monitors connecting and disconnecting themselves while the driver is running.

To avoid confusing the driver you can try using the gpu driver utility to disable the screen before you turn it off and enable it again when you turn it back on. This works for some drivers, it may work for you.

---

### Post by danbaatar on 2009-08-13
I suspected something like that.  I just don't understand.  I'm using the standard Nvidia driver, as best I can tell.  These are the Nvidia packages I have installed:

```
i A nvidia-173-modaliases           - Modaliases for the NVIDIA binary X.Org dri
i A nvidia-180-kernel-source        - NVIDIA binary kernel module source        
i A nvidia-180-libvdpau             - Video Decode and Presentation API for Unix
i A nvidia-180-modaliases           - Modaliases for the NVIDIA binary X.Org dri
i A nvidia-71-modaliases            - Modaliases for the NVIDIA binary X.Org dri
i A nvidia-96-modaliases            - Modaliases for the NVIDIA binary X.Org dri
i A nvidia-common                   - Find obsolete NVIDIA drivers              
i   nvidia-glx-180                  - NVIDIA binary Xorg driver                 
i A nvidia-kernel-common            - NVIDIA binary kernel module common files  
i   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
```

Is there some sort of option I can add to my xorg.conf to control how the driver handles hot-plugging?  Is there any other subsystem that might be taking a hand here (e.g. hald)?

---

### Post by danbaatar on 2009-08-14
I think I've fixed this now.  After digging around a little bit through the available xorg.conf options for the Nvidia driver I found a couple that looked like they would be useful.  I added a them to my xorg.conf Screen section, which now reads:

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    # Cut these 2 lines out to return to normal
    Option         "UseDisplayDevice"  "DFP"
    Option         "UseEdidFreqs"  "false"
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080_60 +0+0; nvidia-auto-select+0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

As I understand it, the first addition:

```
Option         "UseDisplayDevice"  "DFP"
```

basically tells the driver to always act as if there were a digital flat panel monitor connected.

The second:

```
Option         "UseEdidFreqs"  "false"
```

tells the driver to not worry about getting the available frequencies from the monitor, but to instead use the ones found in the Monitor section of the xorg.conf file.

I'm pretty sure that it's the first one that really fixed the problem.  My hypothesis is that the Vizio doesn't handle the re-connection handshake correctly, and so the nVidia wasn't able to properly detect it when it came back on.  In the documentation, that option was described as a solution to a similar problem that occurs sometimes when you use a KVM switch, which basically disconnects the monitor from one computer or another, and then re-connects it later when the user flips a switch.

Maybe I'll go back and try things without one or the other of these options to see what (if any) effect they have individually.  If I do, I'll report back here, just in case it's helpful to someone else.  I'm inclined to stop fiddling with things now, though, and just enjoy the fact that everything seems to be working for a change.

markbuntu, thanks for your thoughts on the subject.  They got me pointed in the right direction, I think.

--dan

---

### Post by danbaatar on 2009-08-22
I spoke way too soon.  This issue is definitely not resolved.  I still have problems with the TV not syncing back with the computer after powering the TV off and then on.

---

