---
title: "Weird Dual Monitor issue with my Latitude E7440"
date: 2014-02-28
forum: Multimedia Software
---

### Post by Modok on 2014-02-28
Short story, Ubuntu 13.10 is seeing my 2 external displays as one large display with a resolution of 3360x1050

Longer Story
I have my Lat E7440 in a docking station with 2 Dell 20" monitors connected via DVI
At first I was seeing my laptop screen as my primary, and one of my external screens was extended to that primary screen and the other external display was a clone of the first. 
So I go into display settings and see this
[ATTACH=CONFIG]250782[/ATTACH]
And there does not appear to be a way to tell it that that giant monitor is actually two. 

I have installed the latest Intel drivers from 
[https://01.org/linuxgraphics/downloads/2013/intelr-graphics-installer-1.0.3-linux](https://01.org/linuxgraphics/downloads/2013/intelr-graphics-installer-1.0.3-linux)
I tried things like removing Xinerama thinking that would help. 
I can't even count the amount of different things I tried. Messing with my monitors.xml file, I tried KDE and it did the same thing. updated xorg. I disabled the built in laptop screen... I just... I'm just at a loss. Can anyone help me with this?


```
xrandr
Screen 0: minimum 320 x 200, current 5280 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+3360+0 (normal left inverted right x axis y axis) 309mm x 173mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 connected 3360x1050+0+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0 +
   3360x1050      60.0* 
   2560x1024      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

```
sudo lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)



```
```
sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:61 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)



```

---

### Post by Nueaf on 2014-03-12
We are experiencing exactly the same issue on a Dell Lattitude E5440. Did you find a solution yet?

---

### Post by evie-blackwell on 2014-07-10
The Dell Latitude uses Display Port MST (Multi Steam Transport) to connect its additional external displays. There is a bug open for this issue part of this issue: [https://bugs.freedesktop.org/show_bug.cgi?id=73694](https://bugs.freedesktop.org/show_bug.cgi?id=73694)

In short, the additional displays are essentially mapped as one large display. A partial  workaround can be found here: [https://bugs.freedesktop.org/show_bug.cgi?id=72795](https://bugs.freedesktop.org/show_bug.cgi?id=72795)

---

