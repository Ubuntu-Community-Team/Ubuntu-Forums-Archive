---
title: "Flickering stripes and restarts of my screen (dual screen setup with xrandr)"
date: 2011-02-08
forum: Multimedia Software
---

### Post by Chrilleee on 2011-02-08
I just installed Xubuntu 10.10 on my desktop computer (signature, gfx: ATI X800) and I'm running it on 2 screens. One 24" ViewSonic vx2435 (as primary) and a 19" Samsung SyncMaster 940B.

When I first started I added this to .xprofile:
> 
xrandr --output DVI-0 --mode 1920x1200 --rate 60 --primary
xrandr --output VGA-0 --mode 1280x1024 --rate 75 --right-of DVI-0
That worked, until I restarted the computer, that's when all the flickering on my ViewSonic (DVI-0) started! As soon as I open up a terminal and drag around the screen there was flickering stripes. And if I moved it much the screen restarted itself, which it did even when just using the other screen.

I tried doing a "cvt 1920 1200 60" and got this:
> 
# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
Setting a new mode to that didn't work, the screen didn't show anything after that.

I know my screen has had problems in Windows with the EDID-info being wrong when using the HDMI-port on it. So I connected it with the VGA and got this Modeline:
> 
154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync
That one took away the flickering and restarting, for the moment! As soon as I restarted it was back! So now I do like this (my .xprofile):
> 
xrandr --newmode "1920x1200_60_EDID"  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync
xrandr --addmode DVI-0 1920x1200_60_EDID
xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
xrandr --addmode DVI-0 1920x1200_60.00
sleep 1
xrandr --output DVI-0 --mode 1920x1200_60_EDID --primary
xrandr --output VGA-0 --mode 1280x1024 --rate 75 --right-of DVI-0
sleep 2
xrandr --output DVI-0 --mode 1920x1200_60.00
sleep 2
xrandr --output DVI-0 --mode 1920x1200_60_EDID
It's really awful but it works, for like half of the times! The other half of the times I need to run the .xprofile again after everything booted up!

And, this is the output of xrandr after trying to set to that mode:
> 
Screen 0: minimum 320 x 200, current 3200 x 1200, maximum 4096 x 4096
VGA-0 connected 1280x1024+1920+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0* 
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
S-video disconnected (normal left inverted right x axis y axis)
DVI-0 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1680x1050      60.0  
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1152x864       75.0  
   1280x720       50.0     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
   1920x1200_60_EDID   60.0  
   1920x1200_60.00   59.9  
It seems like it doesn't want to set to my EDID-mode, or am I wrong?

Anyone having ANY idea how I can fix this?


EDIT: When thinkin about it, I ran Ubuntu for like a year ago. Back then I had to export the EDID-info to a file when connected the screen by VGA, and then, somehow, forcing the DVI to use that EDID-info.

---

### Post by Chrilleee on 2011-02-09
Perhaps this was posted in wrong category? :S

---

