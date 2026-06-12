---
title: "Dual Monitor, Same Type, DIfferent Resolution"
date: 2013-01-28
forum: Multimedia Software
---

### Post by l1th1um on 2013-01-28
Hi,

I'm using dual monitor on Ubuntu 12.10. Both monitor had same brand and type, the only difference is one using DVI cable and others using RGB. The DVI Monitor resolution are 1280x1024 and the other monitor are 1024x768. How I could change the resolution of my RGB monitor to be the same as DVI monitor. Because on NVidia X Server Settings, the RGB monitor don't have option for 1280x1024.

Using **xrandr -q** I got this

```
Screen 0: minimum 8 x 8, current 2304 x 1024, maximum 16384 x 16384
DVI-I-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+
   1360x768       60.0     59.8  
   1152x864       60.0  
   800x600        72.2     60.3     56.2  
   680x384       119.9    119.6  
   640x480        59.9  
   512x384       120.0  
   400x300       144.4  
   320x240       120.1  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 connected 1280x1024+1024+0 (normal left inverted right x axis y axis) 330mm x 320mm
   1280x1024      60.0*+   75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  

```

Then I try this** xrandr --addmode DVI-I-0 1280x1024**

But it returning this
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  37
  Current serial number in output stream:  38
```


My Nvidia Driver is 310.14, and I'm using Geforce GTX 650

---

