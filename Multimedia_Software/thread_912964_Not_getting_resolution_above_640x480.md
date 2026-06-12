---
title: "Not getting resolution above 640x480"
date: 2008-09-07
forum: Multimedia Software
---

### Post by cba.421 on 2008-09-07
I am very new to Linux. So excuse me if I show my noobness in every sentence :)
I  Installed  ubuntu 8.04 a few days ago.

I use Geforce 7200 GS  Graphics Card, and I installed the NVIDIA driver  173.14.12 manually after downloading it from NVIDIA website and restarted. But I have not been getting a resolution above 640x480. 

I  followed this thread  “[SOLVED] Low Resolution Issues Solved (when nothing else works. . . .)” 
[http://ubuntuforums.org/showthread.php?t=884211](http://ubuntuforums.org/showthread.php?t=884211)
and worked accordingly. I have attached my final  Xorg.conf file. 

I used  DVI-D cable ONLY to connect the Graphics Card and my Monitor ( LG 194WT), although I prefer using D-SUB. 

I have also attached screenshots of Nvidia X server program. The most important thing for me looks to be , the Frontend resolution which is not equal to the native resolution.

Somebody please help me out :(

---

### Post by roger_1960 on 2008-09-07
Hi

Have you tried, in terminal

sudo displayconfig-gtk

It will ask for your password and should give you a graphic control panel

Then try changing the model settings there. You should then be able to change the screen resolution. It worked for me when setting up an old laptop with xubuntu.

---

### Post by life_s_good on 2008-09-07
Cba, here are your problems:

```
Section "Device"
 # 
    Identifier     "device1"
    Driver         "nv"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          1
    Option         "CustomEDID" "DFP-0:/home/yaseen/Desktop/edid.bin"
EndSection

Section "Screen"
    Option "AddARGBGLXVisuals" "True"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     640 480
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection
```

You need to enter in a higher resolution in your Modes. Also I *believe* that the nvidia driver you are trying to use is 'nvidia' and 'nv' is the open source driver. You can find instructions on changing these on the forums. Happy trails.

---

