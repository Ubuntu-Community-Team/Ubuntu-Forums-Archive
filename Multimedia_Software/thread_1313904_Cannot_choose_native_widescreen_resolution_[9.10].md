---
title: "Cannot choose native widescreen resolution [9.10]"
date: 2009-11-04
forum: Multimedia Software
---

### Post by danielinteractive on 2009-11-04
Hi all,

I have a fresh install of Ubuntu 9.10 on an IBM T60 laptop with ATI graphics card Radeon Mobility X1400, which is connected to a Samsung SyncMaster 2043 WM via an IBM docking station.

Problem: System / Settings / Screen menu only lists a maximum resolution of 1240 x 1024, and not the native widescreen resolution 1680 x 1050.

Already tried: 

[LIST]
[*]Installing the proprietary ATI drivers from the ATI homepage fails.
[*]Using the fglrx package from the Ubuntu repositories does not bring new resolution choices into the menu (and moreover has poorer "window performance" than the default built in drivers).
[*]System / Admin / Hardware drivers does not list anything which I could choose.
[*]/etc/X11 directory does not feature an xorg.conf file which I could edit (so I am using the default Ubuntu settings I assume).
[*]Interestingly: 
```

daniel@daniel-laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 1680 x 1680
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 459mm x 296mm
   1680x1050      59.9 +
   1280x1024      75.0     60.0* 
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1280x1024+0+0 (normal left inverted right x axis y axis) 287mm x 215mm
   1400x1050      60.0 +   50.0  
   1280x1024      59.9*    60.0  
   1280x960       59.9  
   1280x854       59.9  
   1280x800       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   640x480        59.9     59.4  
DVI-0 disconnected (normal left inverted right x axis y axis)

```shows the native resolutions of both the widescreen VGA and the laptop. So perhaps I can only choose 1280 x 1024 because both monitors feature it? And 1680 x 1050 is only supported by the VGA, so cannot be chosen?
[/LIST]
So my question is: How to setup Ubuntu 9.10 to allow the higher native resolution on the VGA connected via docking station? As the laptop screen is not visible when docked, the laptop screen could be disabled when docked, if that helped.

Attached is my logfile from Xorg.

Thank you very much for your advice!

Daniel

---

### Post by danielinteractive on 2009-11-04
OK, I have understood the issue: I need to deactivate the laptop screen in the menu, and after that, I can select the native resolution of the VGA screen.

---

