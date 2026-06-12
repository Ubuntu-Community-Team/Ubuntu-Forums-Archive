---
title: "Configuring 1366x768 resolution LCD TV for Ubuntu"
date: 2010-05-11
forum: Multimedia Software
---

### Post by justsee on 2010-05-11
Hi there,
I recently upgraded to 10.04, conveniently forgetting to save my carefully handcrafted xorg.conf file, ensuring (many) hours of fun trying to get my non-standard 1366x768 LG 32LC56 32" tv working again with Ubuntu.

There are a lot of dead-end comment threads out there, so I thought I'd jot down some notes which may help someone else, or future me:

On installing the latest version of Ubuntu, I had to install the (version current) restricted Nvidia drivers (System -> Administration -> Hardware Drivers).

After screwing up my xorg.conf a few times, I also made sure to enable networking for all users (System -> Preferences -> Network Connections -> Wireless -> Edit -> Available to all users) and install ssh so I could ssh into the machine when things went wrong, and stay logged in when I ran ```
sudo service gdm restart
``` to test changes to my video configuration.

As a default setting, the Nvidia settings (System -> Administration -> NVIDIA X Server Settings) does not show or allow a 1366x768 mode. To achieve this a custom resolution needs to be specified within the /etc/X11/xorg.conf file.

There is also the [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data") to battle with - the specification data a monitor sends through to a computer, which in my case (and many others) is incorrect. I'll deal with this last.

To specify a correct custom modeline there are a number of approaches to generating one. One I came across was the ```
gtf
``` command. With it you specify your screen dimensions and refresh rate, and it spits out a recommended modeline. In my case I ran ```
gtf 1366 768 60
``` which provided the following details:
```

# 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
Modeline "1368x768_60.00" 85.86 1368 1440 1584 1800 768 769 772 795 -HSync + Vsync

```

This was not exactly what I wanted (generating a modeline for 1368 instead of 1366). There are a bunch of historical posts talking about NVIDIA drivers not supporting anything that is not divisible by 8 (which would include 1366) but thankfully that's not the case in 2010, so I decided to dive into modeline construction.

To calculate the modeline appropriate for my LG TV, [this post](http://www.nvnews.net/vbulletin/archive/index.php/t-74782.html) was a great help. I'd downloaded my tv's manual to determine the hres, vres, and clock (pixel clock) and pe1chl's comment explained how to calculate a custom modeline:
```

You should have said that before. With that information you can calculate the correct modeline immediately. 
clock=85.800
hres=1360
vres=768
so:
Modeline "1360x768" 85.800 1360 aaaa bbbb cccc 768 ddd eee fff +HSync +Vsync 
cccc=clock/hfreq = 85800/47.712 = 1800 (rounded to 8-multiple)
eee = hfreq/vfreq = (85800/1800)/60.0015 = 794 
aaaa and bbbb are between 1360 and cccc (determining horizontal position)
same for ddd and eee.

```

A more detailed explanation of the anatomy of a modeline can be found [HERE]("http://howto-pages.org/ModeLines/").

I added the custom modeline to my xorg.conf as below:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG 32LC56"
    HorizSync       28.0 - 67.0
    VertRefresh     50.0 - 75.0

    ModeLine       "1366x768" 84.75 1366 1440 1584 1776 768 769 772 800 -hsync +vsync
    Option         "DPMS"
EndSection

```

I also specified this as a mode in the Section "Screen" under SubSection "Display" as: Modes "1366x768"

Skipping past endless xorg crashes and configuration changes, I also had to specify some NVIDIA directives to ensure the incorrect EDID information was not being used, and my custom modeline details were. While making these changes I tailed /var/log/Xorg.0.log to check the output. To make the output sing louder, I recommend adding Option "ModeDebug" "true" to your xorg.conf file so you can see exactly what's happening.

There are numerous NVIDIA flags to do with EDID, as detailed [HERE]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-d.html"). The primary ones of interest were initially the Option "UseEDID" "False" to ignore EDID information, and the Option "ModeValidation" ones, many of which people in these forums needed to get their custom xorg.conf config working. However what finally did the trick for me, after many, many hours of headbanging was Option "ExactModeTimingsDVI" "true", which finally forced NVIDIA to read and respect my custom mode details.

At the end of the process I specified a number of directives to get this working in my Screen section (with the commented out options I tried included for my retrospective amusement):

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "UseEdidDpi" "FALSE"
    Option "ModeDebug" "true"
    Option "ExactModeTimingsDVI" "true"
    Option         "ModeValidation" "NoWidthAlignmentCheck, NoDFPNativeResolutionCheck"
#    Option "ModeValidation"    "AllowInterlacecModes, NoTotalSizeCheck,AllowNon60HzDFPModes,NoEdidMaxPClkCheck,NoVertRefreshCheck,NoHorizSyncCheck,NoDFPNativeResolutionCheck,NoVesaModes,NoEdidModes,NoXServerModes,NoPredefinedModes,NoMaxSizeCheck,NoVirtualSizeCheck,NoMaxPclkCheck,NoVertRefreshCheck"
    Option "UseEDID" "False"
    Option         "TwinView" "0"
    SubSection     "Display"
        Depth       24
        Modes   "1368x768"
    EndSubSection
EndSection

```

After all that, I've finally got the old LCD TV operating under 1366x768, which is a relief.

---

### Post by artickl on 2010-05-29
Most important line is:

> Option "UseEDID" "False"

after that - everything work fine!!!

---

### Post by louix on 2010-07-11
Hi

Nvidia xconfig says that my screen is a LG 32LC56 too, but for some reason your xorg.conf doesn't work.

I've modified your xorg.conf so it works for my screen including HDMI sound. I've attracted my modificated xorg.conf. Feel free to use!

I'm not sure that this text *"ModeValidation" "NoWidthAlignmentCheck, NoDFPNativeResolutionCheck* at line 63 needs to be included for the xorg.conf to work, but I've leaved it to be safe.

---

