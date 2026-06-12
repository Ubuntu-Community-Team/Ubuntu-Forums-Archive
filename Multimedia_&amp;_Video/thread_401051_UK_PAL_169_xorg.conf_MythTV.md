---
title: "UK PAL 16:9 xorg.conf MythTV"
date: 2007-04-04
forum: Multimedia &amp; Video
---

### Post by Simoo on 2007-04-04
Hi, I thought I would post up the xorg.conf from my XUbuntu 6.10 MythTV box. I have it running on a standard wide screen tv. I had to get info from different sources, hopefully having it all in one place will help someone. If anyone can improve it,post up!

-------------------------------------------------------------------------------------------------------

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "NoLogo"
        Option          "RenderAccel"           "1"
## Setting this next line to 1 requires you to stop AGPGART from running at boot.
        Option                "NVAGP"                 "1"
## TV out setup.
        Option          "TVStandard"            "PAL-I"
        Option          "TVOutFormat"           "SVIDEO"
## Enables RGB workstation overlay visuals.  This is only supported on Quadro4 and Quadro FX chips (Quadro4 NVS excluded) in depth 24.
        # Option                "Overlay"               "true"
        Option          "XvmcUsesTextures"      "true"
## I set the overscan as 0.0 then use nvidia-settings.
        Option          "TVOverScan"            "0.0"
EndSection

Section "Monitor"
        Identifier   "TV"
## Refresh rate setup - I can't find what I should use so leave it out!
        #HorizSync    15.625
        #VertRefresh  50.0
## Set for 16:9 display. For 4:3 replace 225 with 300.
        DisplaySize 400 225
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
        Monitor         "TV"
        DefaultDepth    24
##Quality will be better if you use the native display resolution. A PAL TV has a basic resolution of 720x576.
        SubSection "Display"
                Depth           1
                Modes           "720x576" "480x576" "350x576" "360x288" "352x288"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "720x576" "480x576" "350x576" "360x288" "352x288"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "720x576" "480x576" "350x576" "360x288" "352x288"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "720x576" "480x576" "350x576" "360x288" "352x288"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "720x576" "480x576" "350x576" "360x288" "352x288"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "720X576" "480x576" "350x576" "360x288" "352x288"
        EndSubSection
EndSection



--------------------------------------------------------------------------------------------------------

Oh and my /etc/X11/XvMCConfig just contains (without quotes) "libXvMCNVIDIA_dynamic.so.1" so the Nvida card's XvMC decoder works.

Not sure if the whole thing will work as a cut and paste as I might have made errors pasting it up here! But should be a good ref.

Simon

---

### Post by [S2] on 2007-04-06
> **Simoo said:**
> 
Section "Monitor"
        Identifier   "TV"
        HorizSync    24.0 - 80.0
        VertRefresh  50.0 - 75.0
# Set for 16:9 display
        DisplaySize 400 225
EndSection



Does the DisplaySize thing still work for you in Xorg 7.2.0? It stopped working for me after the update to Feisty.

---

### Post by Simoo on 2007-04-07
Yes it works for me, with out specifying the 'Displaysize' I get a 4:3 ratio. With it the TV switches to 16:9 and I get a full screen pic.

Although I have not updated to X 7.2. I will just run Edgy (6.10) with the official updates for now, I like to stay a distro behind.

--------------------------------------------------------------------------------------------------------------------
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux melitta 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686
Build Date: 07 July 2006
--------------------------------------------------------------------------------------------------------------------

---

### Post by [S2] on 2007-04-08
> **Simoo said:**
> Yes it works for me, with out specifying the 'Displaysize' I get a 4:3 ratio. With it the TV switches to 16:9 and I get a full screen pic.

Although I have not updated to X 7.2. I will just run Edgy (6.10) with the official updates for now, I like to stay a distro behind.

Thanks for your feedback. It worked for me too in Edgy. It stopped working in Feisty. I had to add

```
Option          "DDC" "false"
```
and
```
HorizSync 30-50
VertRefresh 58-62
```
to my monitor section in xorg.conf

H- and VSync are those of my TV.

---

### Post by Simoo on 2007-04-09
Cool, thats good to know. Cheers.

Where did you get the info about refresh rates for your TV? My manual had none.

---

### Post by [S2] on 2007-04-09
> **Simoo said:**
> Cool, thats good to know. Cheers.

Where did you get the info about refresh rates for your TV? My manual had none.

This worked for me:
```
sudo su
apt-get install read-edid
get-edid | parse-edid
```
But not all TVs report the edid info.

---

### Post by tsu3000 on 2007-11-05
Hi

I am trying to find out the Horiz/Vert refresh rates for my TV as well (PAL Sony 32" VEGA) and tried to install read-edid but it didn't like the fact I am running AMD64 version of 7.04. 

Does the 64bit version exist?

Thanks in advance.

JJ

---

