---
title: "Three monitors, one nVidia card, DVI-i -&gt; DVI-D+VGA splitter"
date: 2010-05-13
forum: Multimedia Software
---

### Post by livewire98801 on 2010-05-13
I can't be the first person to do this, but I can't find any information on it.  Maybe my google-fu is weak.

I have one video card (and no free slots for another) GeForce 8400 GS, and three monitors.  I have a DVI-I splitter cable running to a 24" Samsung (DVI-D) and a 19" Philips (VGA) , and a standard VGA cable running to a 22" Samsung.  

OS is Ubuntu 9.04 Jaunty, 64 bit.

The splitter cable is 'new' (been trying to do this for months), originally I had the two Samsungs working as single connections with Xinerama, no problem.  Then I added the splitter to get a third monitor working.  The 22" Samsung still works, and I know the cable is good.  The video card supports the connection, as my POST and console messages output to the analog connection on the splitter cable, but as soon as X starts, my 19" powers off, and my 'old' two monitor setup stops working.  The nV Control panel doesn't recognise the analog monitor on the splitter cable, and I have tweaked my X config every way I can think of, and I can't get it to work.  I'm hopoing I'm just missing something stupid.

I would really appreciate any help that anyone can give.

Thanks,

Tim


My xorg.conf:
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen      2  "Screen2" RightOf "Screen1"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "1"
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
    VendorName     "Samsung"
    ModelName      "SyncMaster 245bw"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Samsung"
    ModelName      "SyncMaster  2243bwx"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor2"
    VendorName     "Philips"
    ModelName      "19PFL5422D"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Device2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 GS"
    BusID          "PCI:1:0:0"
    Screen          2
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
   Option         "AllowGLXWithComposite" "True"
   Option         "RenderAccel" "True"
   Option         "AddARGBGLXVisuals" "True"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
   Option         "AllowGLXWithComposite" "True"
   Option         "RenderAccel" "True"
   Option         "AddARGBGLXVisuals" "True"
    Option         "metamodes" "CRT-1: nvidia-auto-select +0+0"
    Option         "Rotate" "CCW"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen2"
    Device         "Device2"
    Monitor        "Monitor2"
    DefaultDepth    24
    Option         "TwinView" "0"
   Option         "AllowGLXWithComposite" "True"
   Option         "RenderAccel" "True"
   Option         "AddARGBGLXVisuals" "True"
    Option         "metamodes" "CRT-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "1"
EndSection

```

---

### Post by crystaldafdf on 2011-01-13
> ** said:**
> I've been concerned about the issue, I've got the same [[COLOR=#000000]problem[/COLOR]](http://www.tekbar.net/vi/market-demand/online-survey-festival-ushered-in-the-peak-hopping.html), Have you solved the problem?

---

### Post by livewire98801 on 2011-01-13
No, I eventually gave up a NIC so I could add a second vid card.  I'd still like to see a resolution though (no pun intended), I'm up to four monitors, but could use a fifth.

---

### Post by BicyclerBoy on 2011-01-13
Reconnect two monitors with the splitter & then restart X server..
What's in the /var/log/Xorg.0.log file ??

The splitter cable probably stops the EDID of the second monitor from being reported & then it fails mode validation..

---

### Post by BicyclerBoy on 2011-01-13
What's in the /var/log/Xorg.0.log file ??

The splitter cable probably stops the EDID of the second monitor from being reported & then it fails mode validation..

---

### Post by kitor on 2011-02-06
Hi!
  
I'm trying to do the same, but on Radeon x1950 GT. Got two analog monitors (CRT and LCD) and one digital, CRT connected by DVI-VGA adapter to one of DVI ports, splitter used to connect digital and analog LCDs. 

System is booting on CRT + digital LCD, *radeon* driver in x shows two outputs (xinerama ofc). *radeonhd *uses CRT+analog LCD, shows four outputs (DVI-I_1)/analog, /digital and same for 2, but says that digital is disconnected and I have no idea how to force it. 

On Windows 7 i got working two monitors from splitter simultaneously, so it is possible.

I'll post xorg.0.log, just give me a second

---

