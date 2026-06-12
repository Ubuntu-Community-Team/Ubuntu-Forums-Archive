---
title: "Triple Monitors With Different Video Cards (Nvidia/Radeon)"
date: 2013-10-16
forum: Multimedia Software
---

### Post by eldavar on 2013-10-16
Hello everyone! I'm having trouble getting a third monitor to work properly. All 3 monitors are the same model (Dell 1908fp). 

Before today, I was running just 2 of them on an ATI Radeon HD4350 card (one from the VGA out and one from the DVI). I plugged the third monitor into the integrated VGA port, which is listed as Nvidia GeForce 6100 nForce 405. 

When I turn on the computer, all 3 monitors turn on just fine, all 3 display identical background images, and the login box appears on the new monitor. However, after I log in, only the original 2 monitors connected to the Radeon card actually display anything. The new monitor is just a black screen. 

ARandR detects the new monitor (VGA-2). 
[IMG]https://googledrive.com/host/0B95vSnznZK-adlV0OEVGdzBzYTQ/screenshot-arandr.jpg[/IMG]

If I move the new monitor to the center in ARandR, the middle screen displays what *should* be displayed on the right screen. The monitor is indeed active (the power light is green, not orange, indicating it's active) but it's just a black screen. 

Here's the output of ```
xrandr
```
```
Screen 0: minimum 320 x 200, current 3840 x 1024, maximum 8192 x 8192
VGA-0 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
VGA-2 connected 1280x1024+2560+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
  1280x1024 (0x43)  108.0MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz
  1280x1024 (0x44)  135.0MHz
        h: width  1280 start 1296 end 1440 total 1688 skew    0 clock   80.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   75.0Hz
  1152x864 (0x45)  108.0MHz
        h: width  1152 start 1216 end 1344 total 1600 skew    0 clock   67.5KHz
        v: height  864 start  865 end  868 total  900           clock   75.0Hz
  1024x768 (0x46)   78.8MHz
        h: width  1024 start 1040 end 1136 total 1312 skew    0 clock   60.1KHz
        v: height  768 start  769 end  772 total  800           clock   75.1Hz
  1024x768 (0x47)   65.0MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock   48.4KHz
        v: height  768 start  771 end  777 total  806           clock   60.0Hz
  800x600 (0x48)   49.5MHz
        h: width   800 start  816 end  896 total 1056 skew    0 clock   46.9KHz
        v: height  600 start  601 end  604 total  625           clock   75.0Hz
  800x600 (0x49)   40.0MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock   37.9KHz
        v: height  600 start  601 end  605 total  628           clock   60.3Hz
  640x480 (0x4a)   31.5MHz
        h: width   640 start  656 end  720 total  840 skew    0 clock   37.5KHz
        v: height  480 start  481 end  484 total  500           clock   75.0Hz
  640x480 (0x4b)   25.2MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock   31.5KHz
        v: height  480 start  490 end  492 total  525           clock   60.0Hz
  720x400 (0x4c)   28.3MHz
        h: width   720 start  738 end  846 total  900 skew    0 clock   31.5KHz
        v: height  400 start  412 end  414 total  449           clock   70.1Hz

```Here's the output of ```
lspci | grep VGA
```
```
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6100 nForce 405] (rev a2)
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI RV710 [Radeon HD 4350/4550]

```So, can anyone help me get this to work? The monitor works, so this is definitely a software issue. And as far as I can tell, everything seems to be set up properly.

---

### Post by eldavar on 2013-11-05
Anyone? A little bump here...

So, I'm still stuck with this same problem. I've been working with only the 2 monitors connected to the ATI card, which leaves this 3rd monitor just sitting there doing nothing. I've tried countless different xorg.conf edits, but still no success. I just can't figure out what I'm doing wrong. From everything I've read and everything I've tried, it **should** be working! What am I missing? 

I've edited the xorg.conf file so many times that I'm too frustrated to even look at it again. I've tried creating one from scratch, and I've also duplicated the text provided by other users who claim to have 3 monitors working with 2 different cards (ATI & Nvidia). I've made variations of the xorg file that range from minimalistic and simple, with only the most basic components in each section, and other variations that are ridiculously complex and contain every possible line item. Still, none of them work for me. 

I've tried using the proprietary drivers for both cards, then the open source drivers for both cards, then one proprietary with one open source. Zilch. 

I've tried using Xinerama, Twin View, ZaphodHeads, MergeFB, etc. No luck with those variations. 

So, I would be extremely grateful if anyone can help me get all 3 of these monitors up and running. Below is my current xorg.conf, which only activates the 2 monitors connected to the ATI card and leaves the 3rd one blank. 

```
Section "ServerLayout"    Identifier     "Triple Monitors"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    Screen        2  "Screen2" RightOf "Screen1"
    Option    "Xinerama"    "on"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection


Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
# Left Side Monitor
    Identifier   "Dell-LEFT"
    VendorName   "Dell"
    ModelName    "1908fp"
    Option    "DPMS"
EndSection


Section "Monitor"
# Middle Monitor
    Identifier   "Dell-MIDDLE"
    VendorName   "Dell"
    ModelName    "1908fp"
    Option    "DPMS"
EndSection


Section "Monitor"
# Right Monitor
    Identifier   "Dell-RIGHT"
    VendorName   "Dell"
    ModelName    "1908fp"
    Option    "DPMS"
EndSection


Section "Device"
          Identifier    "ATI1"
    Driver            "ati"
    VendorName    "ATI Radeon
    BusID         "PCI:2:0:0"
    Screen        0
EndSection


Section "Device"
          Identifier    "ATI2"
    Driver            "ati"
    VendorName    "ATI Radeon
    BusID         "PCI:2:0:0"
    Screen        1
EndSection


Section "Device"
        Identifier    "GeForce"
    Driver        "nouveau"        
    VendorName    "NVIDIA Corporation"
    BusID            "PCI:0:0d:0"
    Screen        2
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "ATI1"
    Monitor    "Dell-LEFT"
    SubSection "Display"
        Depth    24
        Modes    "1280x1024"
    EndSubSection
EndSection


Section "Screen"
    Identifier "Screen1"
    Device     "ATI2"
    Monitor    "Dell-MIDDLE"
    SubSection "Display"
        Depth    24
        Modes    "1280x1024"
    EndSubSection
EndSection


Section "Screen"
    Identifier "Screen2"
    Device     "GeForce"
    Monitor    "Dell-RIGHT"
    SubSection "Display"
        Depth    24
        Modes    "1280x1024"
    EndSubSection
EndSection


#Section    "Extensions"
#    Option        "Composite" "Enable"
#EndSection



```
What's interesting is that with this xorg.conf file (and most of the other attempts too), the 3rd monitor plugged into the Nvidia card actually goes into standby mode and is no longer detected by xrandr or arandr. It's as if the computer doesn't even realize the monitor exists (except that lspci does list the Nvidia card). But, if I simply delete the xorg.conf file and reboot the computer, I get the same result (only the ATI monitors display anything) but the 3rd monitor **is not** in standby mode and** is** detected by xrandr. That's weird. 

Anyone care to toss out a suggestion?

---

