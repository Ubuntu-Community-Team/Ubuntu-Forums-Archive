---
title: "Mythbuntu HVR-1800 no video"
date: 2008-11-10
forum: Mythbuntu
---

### Post by cjgcracker on 2008-11-10
Hello,

This is my first post so I apologize if it ends up a bit cluttered.

When setting up Mythtv-backend the tuner card(HVR-1800) is recognized and I am able to add channels on both the /dev/video0 and dvb. Unfortunately when trying to watch TV through mythtv-frontend I get a black screen for a few seconds then it returns me to the main menu. I have also tried to view TV using "mplayer tv://" but receive only a green screen. I haven't even hooked up audio yet so I am unsure if it is working or not. I figured I would start with video and worry about audio when the time comes.  I have searched far and wide to try and resolve this issue on my own but have not had any luck. Any help would be greatly appreciated.

My Setup

Motherboard - P5Q-EM HDMI
Tuner - HVR-1800
Monitor - Samsung LNT-4665F

I have installed the latest v4l-dvb drivers following this post 

[http://ubuntuforums.org/showpost.php?p=6129026&postcount=132](http://ubuntuforums.org/showpost.php?p=6129026&postcount=132)


Some useful info.

Output of dmesg | grep tuner 

```

[   15.470217] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   16.952990] tuner' 0-0061: chip found @ 0xc2 (cx23885[0])
[   16.974039] tuner' 1-0042: chip found @ 0x84 (cx23885[0])
[   17.008890] tda829x 1-0042: could not clearly identify tuner address, defaulting to 60
```

Output of dmesg | grep tv

```
[   15.470211] tveeprom 0-0050: Hauppauge model 78521, rev C1E9, serial# 4876825
[   15.470215] tveeprom 0-0050: MAC address is 00-0D-FE-4A-6A-19
[   15.470217] tveeprom 0-0050: tuner model is Philips 18271_8295 (idx 149, type 54)
[   15.470219] tveeprom 0-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
[   15.470221] tveeprom 0-0050: audio processor is CX23887 (idx 42)
[   15.470223] tveeprom 0-0050: decoder processor is CX23887 (idx 37)
[   15.470224] tveeprom 0-0050: has radio

```

Output of lspci

```
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
02:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
03:00.0 Multimedia video controller: Conexant Systems, Inc. Device 8880 (rev 0f)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
```

xorg.conf

```
Section "Monitor"
        Identifier     "Monitor0"
        VendorName     "Samsung"
        ModelName      "LNT4665F"
        HorizSync       15.0 - 80.0
        VertRefresh     50.0 - 100.0
        Modeline       "1920x1080" 138.500   1920 1960 1995 2083   1080 1082 10$
        Option         "dpms"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Monitor0"
        Device          "Intel GMA X4500HD"
        DefaultDepth    24
EndSection

Section "Module"
        Load "glx"
        Load "dri"
        Load "v4l"    
EndSection

Section "DRI"
        Mode 0666
EndSection

Section "Device"
        Identifier      "Intel GMA X4500HD"
        Driver          "intel"
        VendorName      "Intel"
        BoardName       "G45 [Intel GMA X4500HD]"
        BusID           "PCI:0:2:0"
        Option          "SWCursor" "true"
        Option          "Tiling"  "true"
        Option          "DRI" "true"
        Option          "XVideo" "true"
        Option          "Legacy3D" "true"
        Option "AccelMethod" "EXA"
        Option "VideoOverlay" "off"
        Option "OpenGLOverlay" "on"
        Option "TexturedVideo" "on"
        Option "TexturedVideoSync" "on"
        Option "Textured2D" "on"
        Option "BackingStore" "on"
        Option "UseFastTLS" "1"
        Option "XAANoOffscreenPixmaps" "on"
EndSection
```

---

### Post by cjgcracker on 2008-11-10
Forgot to mention I am running Mythbuntu 8.10

---

### Post by sidimaiga on 2008-11-10
Hi cjgcracker,

I have the same card as you (HVR-1800). but I new to linux and don't know how to use it.
Don't you mind waling me trough the installation. (I would like to be able to watch TV on my Linux Box).

At the same time I could let you know if I running into the same problem. 

Thanks,

sidim,

---

