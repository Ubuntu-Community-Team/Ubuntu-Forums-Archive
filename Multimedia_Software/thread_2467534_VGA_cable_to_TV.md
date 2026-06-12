---
title: "VGA cable to TV"
date: 2021-09-29
forum: Multimedia Software
---

### Post by gilloraymondo on 2021-09-29
Hello,


Ubuntu 20.04
I connected a VGA cable to connect the computer to my TV.
But my TV tells me that there is no signal.

I get this in the console  :

 gilles@gilles:~/Bureau$ find /sys/devices/ -iname edid
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-VGA-1/edid
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-SVIDEO-1/edid
/sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-LVDS-1/edid
gilles@gilles:~/Bureau$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS-1 connected primary 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800      60.00*+  59.99    59.97    59.81    59.91  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
VGA-1 connected (normal left inverted right x axis y axis)
   1360x768      60.37 +
   1280x768      60.25  
   1024x768      60.00  
   800x600       60.32  
   640x480       59.94  
   720x400       70.08  
SVIDEO-1 disconnected (normal left inverted right x axis y axis)
gilles@gilles:~/Bureau$
 
In this LVDS-1 line :        1280x800      60.00*+  59.99    59.97    59.81    59.91            I have a * between 60.00 and + 
I don't see it in the VGA-1 lines... 
I suppose it is the problem.
How can I do ? 
Thank you
[COLOR=#FFFFFF]Ix axis y axis)[/COLOR]

---

### Post by Autodave on 2021-09-30
Your PC is seeing the TV and getting info from the TV.  Have you tried another VGA cable to make sure that your cable is good?  Are you sure that you are choosing the correct input on your TV?

---

### Post by gilloraymondo on 2021-09-30
Hello, 
Yes, I am sure about all this because it worked perfectly with my former computer. 
With Internet, I found this : 
[COLOR=#4B4B49][FONT=Ubuntu]**[FONT=inherit]Display modes[/FONT]**

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][FONT=inherit][FONT=inherit]With two screens, these display modes are available:[/FONT]
[FONT=inherit][FONT=inherit][FONT=inherit]
[LIST]
[*=left][FONT=inherit][COLOR=#808080][FONT=inherit]Join Displays:[/FONT][/COLOR] screen edges are joined so things can pass from one display to another.[/FONT]
[*=left][FONT=inherit][COLOR=#808080][FONT=inherit]Mirror:[/FONT][/COLOR] the same content is shown on two displays, with the same resolution and orientation for both.[/FONT]
[*=left][FONT=inherit][COLOR=#808080][FONT=inherit]Single Display:[/FONT][/COLOR] only one display is configured, effectively turning off the other one. For instance, an external monitor connected to a docked laptop with the lid closed would be the single configured display.[/FONT]
[/LIST]
[/FONT]
[/FONT]
[/FONT]
[/FONT]
[/FONT][/COLOR]
But I have only "single display" working. "Mirror" or "join displays" doesn 't work. 

Any idea ?
Thank you

---

