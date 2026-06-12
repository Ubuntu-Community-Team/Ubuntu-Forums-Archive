---
title: "Intel 4500MHD HDMI problems"
date: 2010-11-09
forum: Multimedia Software
---

### Post by archery on 2010-11-09
When using the HDMI out on my acer 1810tz the output blanks/switches off every 10-30s or so and then comes back on. There doesn't seem to be a pattern though it is less frequent on lower resolutions. I do not have this problem with the VGA out. This has persisted through 2 previous ubuntu installations (9.10, 10.04) but I've ignored it and used the VGA out.

```
$ uname -r
2.6.35-22-generic

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 550mm x 344mm
   1920x1200      59.9 +
   1920x1080      60.0* 
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
HDMI1 connected (normal left inverted right x axis y axis)
   1920x1200      60.0 +
   1920x1080      59.9  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
```
There seems to be the odd thread here
[http://ubuntuforums.org/showthread.php?t=1147885](http://ubuntuforums.org/showthread.php?t=1147885)
and a link to a possible solution here
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

The latter applies to jaunty and doesn't refer to my specific issue. Has anyone else had simialr issues with this chipset (intel 4500MHD) and if so what was the solution?

Many thanks.

---

### Post by archery on 2010-11-12
Ok, it appears no one can help currently. To update I've tried the HDMI out on another monitor and the problem persists so was about to start by updating the xorg drivers from the post below but again the concern is I'll be addressing the wrong problem and this solution is for jaunty and is for performance issues.

[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

I do not have an xorg.conf or rather it has there is no script and the command below does not generate one.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```I'll continue to trawl the forums but any help would be appreciated.

---

### Post by lidex on 2010-11-12
Have a look here:
[http://www.linlap.com/wiki/acer+aspire+1410](http://www.linlap.com/wiki/acer+aspire+1410)
Please post any useful info you may have there for others to reference.

---

### Post by archery on 2010-11-13
Yep been through all that as well but thanks for the input.

---

### Post by archery on 2013-01-20
This is a very old thread but in case anyone comes across the same problem, it resolved with a later version of Ubuntu.

---

