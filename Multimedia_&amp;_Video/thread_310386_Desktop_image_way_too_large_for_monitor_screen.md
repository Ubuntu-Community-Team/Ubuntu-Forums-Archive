---
title: "Desktop image way too large for monitor screen"
date: 2006-12-01
forum: Multimedia &amp; Video
---

### Post by DapperMe17 on 2006-12-01
Xubuntu Edgy 6.10 fresh install
HP Pavilion Monitor -  M70, 17-Inch (D5259A) Display/Monitor
8 MB Nvidia Riva TNT Vanta video card



Completed...
I've successfully installed the nvidia-legacy-glx driver & have successfully updated xserver from "nv" to "nvidia".

I now have an extensive list of settings in my display settings & I get the Nvidia splash screen.



My problem...
Unfortunately, & still troublesome, no matter what display setting I select, the desktop image is still way too large for my monitor screen. Desktop is also off-center.



Could it be...
Could this be that the line & raster frequencies are still not optimized??? Or could it be something else?



Monitor manual specs...
My HP D5259a Pavilion M70 Monitor manual shows line freq at 30-70khz & raster freq at 50-120hz, with dot rate of 110mhz. The max viewable area is 12.8 inches (H) x 9.6 inches (V).



Terminal...
Section "Device"
        Identifier      "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "HWP"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV6 [Vanta/Vanta LT]"
        Monitor         "HWP"
        DefaultDepth    24
        SubSection "Display"
 SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
 EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection





Previous to running Xubuntu Edgy, Windows 98SE was run on this system, with perfectly fit desktop-to-monitor.

Any ideas???





Thanks for any help!

---

### Post by princemackenzie on 2006-12-01
This problem is frequent but I have an easy solution:

> 
Using the gtf Command

The gtf command outputs a ready-to-use Modeline statement for your monitor given the input of resolution and vertical refresh rate of your monitor. To create the correct information for the Modeline statement, look at your monitor's manual and determine its exact native resolution and precise vertical refresh rate for that resolution. For the Envision H193wk, it is listed as 1440 by 900 at 60Hz.

Plug these values into the gtf invocation:

[root@compy ~]# gtf 1440 900 60

yielding:

# 1440x900 @ 60.00 Hz (GTF) hsync: 55.92 kHz; pclk: 106.47 MHz
Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync

The first line is a comment and need not be transferred. Paste or transcribe the Modeline anywhere inside the "Monitor" section that is referred to by the "Screen" section. Then make sure the "Screen" section includes the mode defined by your Modeline statement:

Section "Monitor"
    Identifier    "h193wk"
    Modeline      "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932 -HSync +Vsync
EndSection

(...)

Section "Screen"
    Identifier    "Screen1"
    Device        "nvidia0"
    Monitor       "h193wk"
    Subsection "Display"
        Depth     24
        Modes     "1440x900_60.00"
        ViewPort  0 0
    EndSubsection
EndSection

Running startX should yield an X session matching your monitor's resolution.

Before inserting the Modeline statement into your xorg.conf file, create a copy of xorg.conf so you can revert to the machine generated file if necessary.

If you have a problem after starting X, you may kill the X session by pressing <ctrl-alt-Backspace>. 


I shamelessly :p ripped this from the Caos linux wiki, which is down.  But following those directions should steer you straight.

---

### Post by DapperMe17 on 2006-12-01
Thanks for the info.

As a Linux newbie, can you offer something a little more step-by-step, with the appropriate commands?


Here are the monitor specs, in addition to the prior command prompt info...

Picture tube  	17 inches (43.1 cm), 90 degrees deflection, non-glare, black matrix, light transmission 52% phosphor P22 medium short, 0.28 mm dot pitch
Maximum viewable area 	320 mm (H) x 240 mm (V)

12.8 inches (H) x 9.6 inches (V)
Line (horizontal) frequency 	30&#8211;70 kHz
Raster (vertical) frequency 	50&#8211;120 Hz
Dot rate 	110 MHz
Pedestal 	Tilt: -5 degrees forward,

17 degrees backward

Swivel: -45 degrees left or right

---

### Post by DapperMe17 on 2006-12-02
Does anyone know the modeline for my listed specs? Any help with inputing these to the config file would be greatly appreciated8) 

Thank you

---

