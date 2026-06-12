---
title: "Can't increase refresh rate (twin view)"
date: 2006-08-08
forum: Multimedia &amp; Video
---

### Post by encompass on 2006-08-08
I have the nvidia driver setup according to the envy script (thanks!)
but can't increase the resolution... searching the forms got me this...
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)
(Part 10)
But I don't think it helped... still getting 50 according to ubuntu resolution settings and 60 on the monitors.. I want to push it to 75 cause my eyes can't take it much longer!
This is the relevent part of xorg.conf
```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 204.0
    VertRefresh     43.0 - 75.0
    Option         "DPMS"
EndSection

#Section "Device"
#    Driver         "nvidia"
#    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
#EndSection
Section "Device"
	Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver "nvidia"
	VendorName "Unknown"
	BoardName "NVIDIA GeForce 5200"
	Option "NvAGP" "2"
	Option "NoLogo" "0"
	Option "RenderAccel" "0"
	Option "CursorShadow" "1"
	Option "Coolbits" "1"
	Option "ConnectedMonitor" "crt, crt"
	Option "NoPowerConnectorCheck"
	Option "TwinView" "1"
	Option "Metamodes" "1280x1024,1280x1024; 1280x960,1280x960; 1152x864,1152x864; 800x600,800x600; 1024x768,1024x768; 1280x1024,NULL; 1024x768,NULL"
	Option "SecondMonitorHorizSync" "28-204"
	Option "SecondMonitorVertRefresh" "43-60"
	Option "UseEDID" "False"
	# Option "NoTwinViewXineramaInfo"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024_75" "1056x844_75" "1024x768_75" "800x600_75"
        Viewport 0 0
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1056x844" "1024x768" "800x600"
        Viewport 0 0
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1056x844" "1024x768" "800x600"
        Viewport 0 0
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1056x844" "1024x768" "800x600"
        Viewport 0 0
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024_75" "1056x844_75" "1024x768_75" "800x600_75"
        Viewport 0 0
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024_75" "1056x844_75" "1024x768_75" "800x600_75"
        Viewport 0 0
    EndSubSection
EndSection
```
I have searched the forums... but perhaps I have missed something.

---

### Post by encompass on 2006-08-08
wait a sec... the left says 75 and the right says 60... maybe that is all the right monitor can handle... could be?

---

