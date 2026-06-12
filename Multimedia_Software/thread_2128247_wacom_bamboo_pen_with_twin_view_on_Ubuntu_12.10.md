---
title: "wacom bamboo pen with twin view on Ubuntu 12.10"
date: 2013-03-22
forum: Multimedia Software
---

### Post by asgard2 on 2013-03-22
Hi,  I tried these two possebilities: 
> $ xrandr
Screen 0: minimum 8 x 8, current 3200 x 1080, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
LVDS-0 connected 1280x800+1920+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 269mm
   1920x1080      59.9*+   60.0  
   1680x1050      60.0  
   1280x1024      75.0     60.0  
   1280x960       75.0  
   1280x720       75.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  

$ xsetwacom set "Wacom Bamboo Connect Finger touch" MapToOutput LVDS-0
Unable to find an output 'LVDS-0'.

    But it is not working, does anyone know why?
 [[IMG]http://www0.xup.in/tn/2013_03/13571317.png[/IMG]]("http://www.xup.in/dl,13571317/Bildschirmfoto_-_21.03.2013_-_11:26:24.png/")   
From this Thead: [http://ubuntuforums.org/showthread.php?t=1656089](http://ubuntuforums.org/showthread.php?t=1656089)  

It seems that the thead is dead, because it is assigned to Maverick and Natty.  

Regards, 
 asgard

EDIT:
SOLVED
[http://ubuntuforums.org/showthread.php?t=1656089&p=12570144#post12570144](http://ubuntuforums.org/showthread.php?t=1656089&p=12570144#post12570144)

---

