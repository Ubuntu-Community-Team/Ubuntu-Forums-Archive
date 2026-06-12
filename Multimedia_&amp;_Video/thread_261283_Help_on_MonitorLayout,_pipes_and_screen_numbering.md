---
title: "Help on MonitorLayout, pipes and screen numbering"
date: 2006-09-20
forum: Multimedia &amp; Video
---

### Post by feffemannen on 2006-09-20
Hi!

**Qs**:
Can anyone explain (or point me to some document explaining) what the "MonitorLayout" option *really* does in xorg.conf? Also, what does the "Screen N" in the Device-section *really* do? And how does that number connect with the "Screen N screen-id" in the ServerLayout-section? What does Pipe A and Pipe B mean? 

**Background**:
I'm trying to get an external monitor (Samsung SyncMaster B203, connected to the DVI-port on the docking station) to work with my Dell D620 laptop (with an Intel 945GM chipset). It works quite well, however I get the laptop monitor as display :0.0 and the external as :0.1 (I'm not running xinerama), I really would like to get my external monitor as the primiary, i.e., as display :0.0. I've tried *a lot* of different combinations of MonitorLayout and Screen numbers, but without success.


Here's relevant sections of my xorg.conf:
```

Section "Device"
        Identifier      "Intel 945GM Internal LCD"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen 0
        Option  "MonitorLayout"         "DFP,LFP"
EndSection

Section "Device"
        Identifier      "Intel 945GM External DVI"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen 1
        Option "MonitorLayout"  "DFP,LFP"
#       Option "DevicePresence" "yes"   
EndSection

Section "Monitor"
        Identifier      "Laptop Monitor"
        Option          "DPMS"
        #HorizSync      28-72
        #VertRefresh    43-60
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        #HorizSync      31-75
        VertRefresh     40
EndSection

Section "Screen"
        Identifier      "External Screen"
        Device          "Intel 945GM External DVI"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050" 
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Internal Screen"
        Device          "Intel 945GM Internal LCD"
        Monitor         "Laptop Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          0 "Internal Screen" 0 0
        Screen          1 "External Screen" RightOf "Internal Screen"  
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection


Section "ServerFlags"
#       Option "xinerama" "true"
EndSection


```

---

### Post by motin on 2006-09-20
You should look into "man i810". It will explain "MonitorLayout" and also introduce you to an option called "FlipPrimary". 

Happy hunting!

---

### Post by feffemannen on 2006-09-20
> **motin said:**
> You should look into "man i810". It will explain "MonitorLayout" and also introduce you to an option called "FlipPrimary". 


Many thanks for your reply!

I've tried to read TFM but it doesn't explain about pipes, heads and screen numbers. It least I couldn't find it.

Regarding the FlipPrimary, it is squarely ignored by my X-server. The log says something about "Ignoring Option FlipPrimary" (or similar).

f

---

### Post by motin on 2006-09-20
> **feffemannen said:**
> Many thanks for your reply!

I've tried to read TFM but it doesn't explain about pipes, heads and screen numbers. It least I couldn't find it.

Regarding the FlipPrimary, it is squarely ignored by my X-server. The log says something about "Ignoring Option FlipPrimary" (or similar).

f

Aha, maybe you should have been more clear on where your previous "research" was performed. 

For an in-depth article/tutorial on pipes and MonitorLayout etc I would suggest resources like tldp.org and/or joining the development mailing list for the i810 drivercollection or similar. If you find anything useful - be sure to post it here :)

---

### Post by feffemannen on 2006-09-21
> **motin said:**
> Aha, maybe you should have been more clear on where your previous "research" was performed. 
Right. Sorry...

> **motin said:**
> For an in-depth article/tutorial on pipes and MonitorLayout etc I would suggest resources like tldp.org and/or joining the development mailing list for the i810 drivercollection or similar. If you find anything useful - be sure to post it here :)

I haven't found anything yet. But I did succeed with my task using "FixedPipe" and changing the ordering of the screen numbers. Not shure why though...

Here's the relevant sections from my xorg.conf:

```
Section "Device"
        Identifier      "Intel 945GM Internal LCD"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen 1
        Option  "MonitorLayout"         "DFP,LFP"
        Option "FixedPipe"      "A"
EndSection

Section "Device"
        Identifier      "Intel 945GM External DVI"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Screen 0
        Option "MonitorLayout"  "DFP,LFP"
         Option "FixedPipe"      "A"
#       Option "DevicePresence" "yes"
EndSection

Section "Monitor"
        Identifier      "Laptop Monitor"
        Option          "DPMS"
        #HorizSync      28-72
        #VertRefresh    43-60
EndSection

Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        #HorizSync      31-75
        VertRefresh     45
EndSection


Section "Screen"
        Identifier      "External Screen"
        Device          "Intel 945GM External DVI"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Internal Screen"
        Device          "Intel 945GM Internal LCD"
        Monitor         "Laptop Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"  
        Identifier      "Default Layout"
        Screen          0 "External Screen" 0 0
        Screen          1 "Internal Screen" LeftOf "External Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection


Section "ServerFlags"
#       Option "xinerama" "true"
EndSection


```

f

---

