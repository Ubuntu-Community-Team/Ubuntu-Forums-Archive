---
title: "Monitor out of range. Why?"
date: 2010-06-15
forum: Multimedia Software
---

### Post by Moozillaaa on 2010-06-15
That's the message; it was fine yesterday.

Today, out of range. 

I reconfigured X, it loaded in a low resolution environment, I re-enabled ATI driver, re-booted, and out of range again.

It's working fine in Windows. At this rate, Windows will never go away... :confused:

I do Hardy LTS

---

### Post by dabl on 2010-06-15
That message comes from the monitor.  It means "I am not getting a valid signal from the graphics chip".  Usually it means the horizontal and/or vertical refresh rates are outside the monitor's capabilities.

Maybe your video driver is not installed, or not installed correctly. Possibly a "modeline" in your xorg.conf file, with horizontal and vertical refresh rates, is needed.

---

### Post by Moozillaaa on 2010-06-15
If I boot default configuration (below), then attempt to load the ATI accel graphics driver, then it reverts to 'Out of Range' at reboot.

Where does the 'modeline' go in my config file?

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection

---

### Post by dabl on 2010-06-15
You need to research the specs for your display/monitor model, to learn the maximum horizontal and vertical refresh.  Then follow these:

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

[http://ubuntuforums.org/tags.php?tag=modeline](http://ubuntuforums.org/tags.php?tag=modeline)

---

### Post by Moozillaaa on 2010-06-15
I have those pages open on other tabs (done it).

I just listed hardware in the terminal...

** *-display UNCLAIMED**
                description: VGA compatible controller
                product: Radeon HD 3300 Graphics
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: vga_controller bus_master cap_list
                configuration: latency=0



What does THAT mean???


edit:
I just tried to load older kernel versions, and they loaded in low resolution graphics mode.

---

