---
title: "Dual Monitor Help"
date: 2007-04-30
forum: Multimedia &amp; Video
---

### Post by Nythain on 2007-04-30
I have successfully figured ALMOST everything out... but now my main monitor is trying to draw to unconfigurable displays over its main display... keep in mind i got the second monitor doing EXACTLY what i want it to (seperate x screen, its own panels, own resolution, yakuake loads on the appropriate monitor now)
I will attach a screenshot to show you what my main monitor is doing now, any more help would be great

now to throw up my xorg.conf and see if anyone can make any sense out of it and suggest any edits or question any of my modifications to help me get this goin right... im ALMOST there

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Hansol"
    HorizSync       30.0 - 96.0
    VertRefresh     47.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "STAC Electronics KDS VS-70"
    HorizSync       30.0 - 72.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          0
    Option         "TripleBuffer" "true"
    Option         "RenderAccel"  "true"
    Option         "AllowGLXWithComposite"  "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
    BusID          "PCI:2:12:0"
    Screen          1
    Option         "TripleBuffer" "true"
    Option         "RenderAccel"  "true"
    Option         "AllowGLXWithComposite"  "true"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor1"
    DefaultDepth    24
    #Enable 32-bit ARGB GLX Visuals
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "Enable"
    Option "RENDER" "Enable"
EndSection

```
so yeah, any help in cleaning that up or recomendations on options for different sections to add/change/remove would be much appreciated

---

### Post by Nythain on 2007-04-30
ok, so now a whole new problem... when i do something on one, both lag and get choppy, such as browse the web on the main while watching a dvd on the other... is this due to xinerama being enabled... i heard its incredibly slow and doesnt support much in the way of both displays utilizing things like overlays and composite rendering at the same time, at least i think thats how i read it... so many sites saying so many different methods, using so many different options to do the same thing... its all so confusing, but so far completely useless untill i can get them both to run at decent performance

---

### Post by Nythain on 2007-04-30
ok, problem 1 and 2 solved by turning off xinerama... now i have two completely independent screens with thier own panels, backgrounds, running apps, and i cant move anything from one to the other cept my mouse, thats a good thing... still working on this reource issue... im runnin a p4 2.0ghz with 768 megs of ram and that nvidia fx5200 with like 256megs of ram... amd i just trying to do to much here or can anyone notice anything else screwy with my xorg.conf... ill continue to make tweaks and adjustments untill i get it right... im thinking about turning off a few things in xorg that were originally there to run beryl, wich i dont run anymore due to impracticality, instability, and resource limitations

---

### Post by bobby567 on 2007-05-01
Have you tried a place like [www.winfiles.com](www.winfiles.com) ?  Some cards just don't support dual monitors...was this card actually made by Cirrus Logic, or is it a CL chip on another manufacturer's card? one or the other should be able 
to provide you with drivers...whether they support multiple display is another story. 
 
Alex @ [web page design]("http://www.webdesigningcompany.net")

---

### Post by Nythain on 2007-05-01
have successfully figured ALMOST everything out... but now my main monitor is trying to draw to unconfigurable displays over its main display... keep in mind i got the second monitor doing EXACTLY what i want it to (seperate x screen, its own panels, own resolution, yakuake loads on the appropriate monitor now)
I will attach a screenshot to show you what my main monitor is doing now, any more help would be great
The first screenshot is my main monitor, obviously drawing two background images from previous xsessions and x displays, that i cant change now
The second screenshot is the secondary monitor doing exactly what i want it to do

---

