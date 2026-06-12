---
title: "LG 32LC2R LCD TV Resolution problem"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by petrosy on 2007-06-03
Hi All

I have been trying to setup my Ubuntu on my LCD TV. The res of the TV is 720p 1366x768. I have installed the NVIDIA drivers and that works fine however it only supports a resolution of 720x480 or 640x480. I have tried the NVidia configuration tool with no luck. I even manually editted my xorg.conf and removed all other res types and manually inserted the correct on. Still with no luck

I am connecting straight from my DVI --> HDMI. I really don't want to go an buy RGB cables and try and set it up as a TV. 

Anyone had similar issues with LCD TV's and how did you resolve it? This is my one of my final hiccups of binning MCE.... Need to make my HTPC idiot proof as my flatmate and MS is a bad combination ;)

Any help will be much appreciated.

Regards
Petros

---

### Post by birkensteen on 2007-06-03
Well... this might not be exactly what you need but it may help... I went around and around on so many different searches and utilities before i found some random page where a guy had posted about 75 modelines. I knew I wanted to send my TV a (something)x768 so I just commented/uncommented until the one you see below hit it. I certainly wish I could remember where that modeline list was!

There are some other slightly relevant things in here too... now that I look at it I could tighten it up a bit.

The nice thing about it is that when in the Desktop I get full screen, no overscan, and decent font sizes. When running mythtv I set the myth output to 1280x720 and my TV thinks it's getting a 720P signal.

Oh, it's a Vizio 32-inch and I'm using a DVI-to-HDMI cable.

```

mythtvserver:~$ cat /etc/X11/xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Device"
        Identifier      "NVIDIA GeForce 6200"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
#       Option "ModeValidation" "NoDFPNativeResolutionCheck"
EndSection

Section "Monitor"
        Identifier      "Vizio VX32L"
        Option          "DPMS"
        HorizSync       31-60
        VertRefresh     59-86
        UseModes        "Modes[0]"
EndSection

Section "Screen"
        Identifier      "Screen Vizio"
        Device          "NVIDIA GeForce 6200"
        Monitor         "Vizio VX32L"
        Option "RenderAccel" "true"
        Option "ExactModeTimingsDVI" "true"
        Option "ModeValidation" "NoEdidMaxPClkCheck,NoDFPNativeResolutionCheck"
#       Option          "DPI"           "65 x 75"
        Option          "UseEDIDDpi"    "FALSE"
        Option          "DPI"           "100 x 100"
        DefaultDepth    24
        SubSection      "Display"
           Depth                24
           Modes                "1368x768" "1366x768" "1360x768" "1216x684" "800x600" "640x480"
        EndSubSection
EndSection

Section "Modes"
  Identifier   "Modes[0]"
# ModeLine "1366x768" 85.5  1366 1414 1526 1798 768 771 777 795 +hsync -vsync
# ModeLine "1368x768" 84.97 1368 1400 1720 1752 768 783 791 807
# ModeLine "1366x768" 88.03 1366 1424 1680 1816 768 770 782 808
# Modeline "1366x768" 72.25 1366 1416 1448 1528 768 771 781 790 +hsync -vsync
# Modeline "1360x768" 85.50 1360 1424 1536 1792 768 771 777 795 +Hsync +Vsync
# Modeline "1360x768" 84.50 1360 1392 1712 1744 768  783  791  807
# Modeline "1360x768" 85.750 1360 1432 1568 1776 768 771 776 798 -hsync +vsync

    ModeLine "1360x768" 85.50 1360 1424 1536 1792 768 771 777 795 +hsync +vsync

# ModeLine "1216x684" 74.250 1216 1356 1396 1650 684 704 709 750 +hsync +vsync
# Modeline "800x600" 97.59 800 856 944 1088 600 601 604 650
# Modeline "800x600" 96.89 800 856 944 1088 600 601 604 650
# Modeline "800x600" 96.18 800 856 944 1088 600 601 604 650
Modeline "640x480" 62.12 640 680 752 864 480 481 484 521
Modeline "640x480" 61.55 640 680 752 864 480 481 484 520
Modeline "640x480" 61.10 640 680 752 864 480 481 484 520
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Screen Vizio"
EndSection

```

---

### Post by petrosy on 2007-06-03
Excellent... I will try that when I et home tonight.

Thanks
Petros

---

### Post by petrosy on 2007-06-04
Seems to be almost working. I am getting correct resolution. However I have some over-scan. I will search around for the correct setting and post the file once done

Thanks for the help birkensteen!

---

### Post by birkensteen on 2007-06-04
Right on! My first happy customer!
Those front/back-porch settings are pretty hard to just guess at. If you can boot into Windows on that box you may have some luck with powerstrip from entechtaiwan.net

---

### Post by petrosy on 2007-06-04
Right.. interesting site. I will give that a go later. I have found MODE string for my TV apparently on the net. 

So hopefully between the 2 I should get that going later. Then its trying to configure my generic DVB-T card. However I might just throw money at that problem and buy a out the box supported one.

Regards
P

---

### Post by petrosy on 2007-06-06
Still nothing.... close. Getting higher res but pic does not fit. 

Apparently Fedora Core has a monitor scan util during setup. Might just install that and grab a copy of xorg.conf then reload Ubuntu. The beauty about linux is that you can install and reinstall in fraction of the time it takes to rebuild XP :)

---

### Post by j4ni on 2007-06-09
I'm having the same problem with LG 37LC2R. So I would appreciate if you could post the  solution when you solve this problem. Could you also paste the best configs you have managed to create so far?

   - j4ni

---

### Post by grege on 2007-06-09
I have a Samsung TV and the manual states that even though the panel is 1366x768 the PC resolution should be set to 1360x768. This may help with your overscan issues

Mine works perfectly at this setting, but only with the fglrx driver, not the at, or vesa. I had a NVidia and again it would only work with the nvidia driver not with nv.

Also you must have a VGA cable with filters, the cheap ones without filters (meant to be monitor extensions) will lead to ghosting.

:)

---

### Post by j4ni on 2007-06-13
Grege vga cable?  petrosy was using dvi2hdmi-cable?  But thanks for the resolution tip.
Petrosy have you had any success with the overscan issue?

-j4ni

---

### Post by petrosy on 2007-10-25
No Success.... I have put it on hold for the time being. Will attempt it again with Ubuntu 7.10.

---

### Post by thkouk on 2008-02-05
I am facing a resolution problem with LG 27LC2R (1368X700 according to the manual) and an an ATI 9600 video card.

I use the alternate installation cd and following the default installation procedure, I get an out of sync screen that shows only stripes of artifacts.

To begin the installation, I have to switch the installation resolution to 640X480. I didn't have the time to complete the setup using the advanced procedure of the alternate CD, but I am not very optimistic. I tried to install OPENSUSE 10.3 and PCLinuxOS before and although they installed they didn't work at the correct resolution for the TV screen and the result was the "snow"  on the screen I described before.

Any ideas on how I should do the setup? Maybe try to set it up via the PC screen and afterwards try to alter the configuration to work on the TV?

Any advice will be much appreciated! :(

---

