---
title: "Ubuntustudio + nvidia + madwifi issue"
date: 2009-03-26
forum: Multimedia Software
---

### Post by instantkarma on 2009-03-26
Hi everybody,

I just installed ubuntustudio-audio from the repos and I've been experiencing rowdy behavior from my machine.
After installation completed, I rebooted, and when x started up the screen resolution was 800*600 (and not the normal 1024*768) and wifi was not working. I was only able to re-install madwifi after installing linux-headers-2.6.24-23-rt and linux-restricted-modules-2.6.24-23-rt.
Long story short, I've installed and uninstalled the nvidia driver both thru envy about three times (all the while re-installing madwifi a couple of times in between because after installing nvidia wifi disappears) and finally thru system->administration->hardware drivers. Nothing has changed. My resolution is a catastrophe and I assume nvidia isn't installed properly.
Also, the mousepad doesn't have double-click since this issue has arisen and in fact the pad doesn't work at all except for moving the arrow.

here's xorg.conf:

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        SubSection "Display"
                Depth   24
                Virtual 640     480
                Modes           "640x480@60"
        EndSubSection
        Defaultdepth    24
EndSection

Section "Screen"
        Identifier      "screen1"
        Device          "device1"
        Monitor         "monitor1"
        Defaultdepth    24
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:0:18:0"

        Driver          "nvidia"
        Screen  0
        Option          "NoLogo"        "True"
EndSection

Section "Device"
        Identifier      "device1"
        Boardname       "vesa"
        Busid           "PCI:0:18:0"
        Driver          "nv"
        Screen  1
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

Section "Monitor"
        Identifier      "monitor1"
        Gamma   1.0
EndSection

Section "Extensions"
EndSection


```

I really need help with this so if anyone can please help out it would be very appreciated as I've spent most of my day dealing with this. I'm sure it's not such an issue as I've seen somewhat similar posts regarding ubuntustudio and nvidia with relation to restricted-modules and such but I am really very limited in my Linux knowledge - hence this plea to you.

---

### Post by aeiah on 2009-03-26
i believe the reason things messed up is because ubuntu studio has its own realtime kernel for better audio production. of course, this means that any compiled drivers and modules will need to be recompiled and/or reinstalled. your mouse issue sounds odd though. is there anything particularly special about your mouse?

if you revert back to your prior kernel at the grub screen things should work as normal. of course, this doesn't fix the issue, it just reverts to your old kernel, which won't be as good for audio work as the realtime one.

---

### Post by instantkarma on 2009-03-26
> **aeiah said:**
> i believe the reason things messed up is because ubuntu studio has its own realtime kernel for better audio production. of course, this means that any compiled drivers and modules will need to be recompiled and/or reinstalled. your mouse issue sounds odd though. is there anything particularly special about your mouse?

if you revert back to your prior kernel at the grub screen things should work as normal. of course, this doesn't fix the issue, it just reverts to your old kernel, which won't be as good for audio work as the realtime one.

Mouse issue resolved. I uninstalled nvidia from system->admin->hardware drivers (unticked the box), rebooted and mouse is fine. No nvidia though. 

So what your saying is that I have to recompile/reinstall nvidia for this current apparently audio-superior kernel? How do I do that? [This way?]("https://help.ubuntu.com/community/NvidiaManual")
I've already tried envy numerous times to no avail...
 
Also, how do I revert back to the old kernel? And if I do so, will there be a noticeable effect on ubuntustudio performance?

Thanks for helping me out here. thumbs up.

---

