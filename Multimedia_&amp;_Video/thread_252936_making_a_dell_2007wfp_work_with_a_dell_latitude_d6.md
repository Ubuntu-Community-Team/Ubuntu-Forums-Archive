---
title: "making a dell 2007wfp work with a dell latitude d620"
date: 2006-09-07
forum: Multimedia &amp; Video
---

### Post by froydnj on 2006-09-07
I just received a new Dell Latitude D620 with a Dell 2007WFP monitor.  The D620 has a Nvidia Quadro NVS 110M graphics card with 256MB of RAM.  I'm running Ubuntu 6.06 due to the luck I had with setting up its predecessor on a desktop a year or two ago.

The setup I'd like to have (and which was easily accomplished with my last laptop, a PowerBook) is for the monitor to act as a seconday display at its full 1680x1050 resolution.  From what I've read, this requirement means that the two monitors will act as different screens--I'll be able to move my mouse back and forth between them, but I'll not be able to drag windows back and forth.  This is fine.

Unfortunately, I can't get this setup to work.  When I use the 'nvidia' driver, I can get close to what I want, but the 2007WFP will not display at 1680x1050; it insists on using the laptop's resolution of 1440x900 or something slightly smaller (1280x800).  Relevant bits of /etc/X11/xorg.conf follow:

```
Section "Device"
        Identifier      "nvidia0"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          0
EndSection

Section "Device"
        Identifier      "nvidia1"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Screen          1
EndSection

Section "Monitor"
        Identifier      "LaptopScreen"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Monitor"
        Identifier      "FlatPanel"
        Option          "DPMS"
        HorizSync       30.0 - 83.0
        VertRefresh     56.0 - 76.0
        Modeline "1680x1050" 147.14 1680 1784 1968 2256 1050 1051 1054 1087
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "nvidia0"
        Monitor         "LaptopScreen"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "nvidia1"
        Monitor         "FlatPanel"
        DefaultDepth    24
        SubSection "Display"
                Viewport 0 0
                Depth 24
                Modes "1680x1050" "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Screen0"
        Screen          1 "Screen1" RightOf "Screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection
```

I have seen a lot of different ModeLines for the Dell 2007WFP--some even on this forum--and have had no luck with any of them.  The above ModeLine is the output from 'gtf', minus the '-HSync +Vsync' at the end, as these seem to cause parsing problems when X starts up.

The read-edid utility fails, so I can't get any decent information from that, either.

If I instead try my luck with the 'nv' driver, I can't even get X to start unless I comment out the declaration of the second screen in the ServerLayout section.  (The error message is something about the requested entity already being in use, which I take to mean that the nv driver is not smart enough to know that there exists both a laptop screen and an external VGA connector to display to.)  Using the 'nv' driver, I can also get the display at least cloned between the laptop screen and the external LCD, but it shakes horribly on the external LCD and is unusable.

Any suggestions?  Do I need to tell X a bit more about my 2007WFP?  I keep telling myself that it should not be this hard, but clearly it seems to be. :)

Thanks in advance,
-Nathan

---

### Post by neum on 2006-09-13
Yes it is that hard. 

I've got a d620 as well and trying to make another monitor work with it. In windows its as simple as clicking extend my windows desktop onto this monitor. In Linux... who knows. But I'll update if I ever get mine to work.

---

### Post by neum on 2006-09-13
I'm going to try this once I get home.

[http://ubuntuforums.org/showthread.php?t=221174&highlight=d620](http://ubuntuforums.org/showthread.php?t=221174&highlight=d620)

Scroll down to "A (Very) Short nVidia TwinView HowTo:"

I'll let you know if it works.

---

