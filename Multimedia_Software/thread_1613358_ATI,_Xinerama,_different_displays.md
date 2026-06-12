---
title: "ATI, Xinerama, different displays"
date: 2010-11-04
forum: Multimedia Software
---

### Post by rabby_ on 2010-11-04
Hi,

With 2 different displays, I wonder how to modify the refresh rates.
Currently I see one screen well and the other has "snow" on white backgrounds.

I configured the video card to dual screen with ATI Catalyst -> Xinerama active.
After activating Xinerama, there is no more option to change the refresh rate and when deactivating, restarting with single displays, changing the refresh rate and re-activating Xinerama does not seem to work :-(

So maybe it's easiest to set the rate(s) within the **xorg.conf** which is tiny today:
> Section "Screen"
    Identifier    "Configured Screen Device"
    Device    "Configured Video Device"
    SubSection "Display"
        Virtual    3600 1080
    EndSubSection
EndSection

Section "Device"
    Identifier    "Configured Video Device"
EndSection
Here comes what **xrandr** is telling me:
> Screen 0: minimum 320 x 200, current 3600 x 1080, maximum 3600 x 1080
DVI-1 connected 1920x1080+1680+0 (normal left inverted right x axis y axis) 543mm x 306mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
DVI-0 connected 1680x1050+0+30 (normal left inverted right x axis y axis) 473mm x 296mm
   1680x1050      60.0*+   60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
Thanks for advice!

---

