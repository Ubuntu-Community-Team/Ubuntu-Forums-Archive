---
title: "ubuntu thinks 1024x768 is 1360x768"
date: 2010-06-27
forum: Multimedia Software
---

### Post by Kylerobhew1 on 2010-06-27
I am using an LCD TV via VGA connector as my display, I have limited resources so I would like to find a software fix for this problem. It all starts with my xorg.conf, I have my preferred mode set to 1024x768_60 because without an HDMI cable that is the highest resolution my TV can display. when I boot to 1024x768 its really displaying 1360x768 even though display properties says it's at 1024x768. I know this because When I hot-swap it to another monitor (also a TV) the TV says its displaying 1360x768 but display properties says it's at 1024x768 (I hope your still with me). 

There seems to be a problem with the mode alias for 1024x768, according to display settings 1024x768 is just an alias for 1360x768 when it's plugged into that TV.:confused:

Also, when I connect to the TV I used to view the resolution and click detect monitors, display settings displays all resolutions properly including 1024x768, in which case I am able to hot-swap the VGA connector to my other TV (the one with problems) and view it at 1024x768 properly until I restart then it reverts back to 1360x768 but display settings still insists that I'm viewing 1024x768.

Any help would be appreciated, I have been inching my way through this problem for a good 10 hours and it has been so confusing to say the least. I think I'm sprouting grey hairs. my xorg and lspci output are listed below, I'm using karmic with open source drivers. i have 3d accel and compositing working properly this is just the last piece of the puzzle and I'm stuck.

lspci
```

00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Network controller: RaLink RT2561/RT61 802.11g PCI
00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0a.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
00:0b.0 USB Controller: NEC Corporation USB (rev 43)
00:0b.1 USB Controller: NEC Corporation USB (rev 43)
00:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

```xorg
```

#Section "Device"
#    Identifier    "Configured Video Device"
#    Driver        "vesa"
#EndSection

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "XAANoOffscreenPixmaps"
        Option            "BusType" "PCI"
        Option             "AGPMode" "1"
EndSection

Section        "Monitor"
    Identifier    "Toshiba Regza"
    VendorName    "Toshiba"
    ModelName    "hd32us"
    Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
    Option          "PreferredMode"        "1024x768_60.00"
    Option         "DPMS"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth     24
    SubSection     "Display"
        Modes         "800x600" "1024x768"
    EndSubSection
EndSection

```

---

### Post by Kylerobhew1 on 2010-06-27
Come on where's the community when we need them, I have been a loyal ubuntu user for 3 years and have offered many solutions for people on these forums (from various handles) and i have yet to have someone even so much as respond to one of my questions. 

I know there's a way to replace the mode alias for 1024x768, I have seen the soloution using xrandr in the past when I upgraded pc's last time but I cant find the same tutorial. I know someone in the comunity has a soloution to my problem, it's just rare for this to happen with the new xorg in karmic, but it still happens. I don't need someone to spoon feed me the information, I know my way around in ubuntu, I just need someone to tell me how to change a mode-alias for a corrupt edid signature in ubuntu, is that so hard to ask.

The first person to respond (even just a bump) gets popcorn :popcorn:.

---

### Post by Kylerobhew1 on 2010-06-27
Well in any case, I donate every month and I probably wont for a while unless I can get this working properly, and if I have to fix everything on my own I wont even so much as consider donating another cent. Not one to bragg about donating or hold things over peoples heads for that matter, it just doesn't seem like my money is going to any good use. I am utterly disappointed.

---

