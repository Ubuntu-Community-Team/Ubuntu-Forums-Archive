---
title: "BIG PROBLEM WITH DUAL MONITOR in 10.04. Very much Frustrated"
date: 2010-05-09
forum: Multimedia Software
---

### Post by BrownHorse on 2010-05-09
Hello Guys,

Here is my problem. When I hook up my laptop to 62" LCD TV via HDMI, the video output on the TV has resolution of 640x480 (4:3). Also same screen is displayed on both laptop and TV. 

Here is what I like to do: How to I change the resolution from 640x480 to 1280x1024(16:9) ? I only want video output on TV and not laptop. Its displaying on both at the moment


I went to System>Preference>Monitor and highest resolution it has is 640x480 when I have my TV plugged into HDMI port of Laptop. Also this monitor utility does not have any option to turn off secondary display(Laptop) and only allow video on primary (TV)

Dual monitor worked great in Vista but I am having hard time getting it work properly in Ubuntu :(

PLEASE HELP!!!

---

### Post by shankaranand on 2010-05-10
I have the same problem too.. Did you find any solutions

---

### Post by BrownHorse on 2010-05-12
[QUOTE=shankaranand;9271288]I have the same problem too.. Did you find any solutions[/QUOTE

I dont know, I just plugged it my laptop to LCD tv and it allowed me to set the resolution to what I want. I was able to able to turn off secondary display (Laptop) and only allow the output on TV. It started to work automatically without any issues!

Linux Rules!!!!

---

### Post by jerryablan on 2010-05-12
Check out the wiki page I just made regarding this. It may help. No promises...

[http://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor](http://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor)

---

### Post by troll1602 on 2010-05-12
Hey, so I think I was having the same problem so here is a quick explanation of my setup and what I did.

First off, I am using an nVidia GeForce GT240 graphics card that has 2 DVI outputs. I have two monitors setup each on a DVI port.

Well, one of the monitors has an HMDI port and came with a HMDI to DVI adapter to work with the graphics card. When I tried to use that I got the same exact problem as described above.

At first I thought it was an issue with the adapter, but after hearing that you guys has the same problem with HDMI perhaps it is something specific with 10.04 and HDMI output, but I guess you probably already knew that :-)

Anyway my solution was to just use a different port. Sorry if that isn't too helpful...

---

### Post by troll1602 on 2010-05-12
Here are a few other threads I found with the same problem but on past versions of Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1118253](http://ubuntuforums.org/showthread.php?t=1118253)
[http://ubuntuforums.org/showthread.php?t=1281717](http://ubuntuforums.org/showthread.php?t=1281717)

---

### Post by stunted on 2010-05-13
Seems to work for me, open a terminal and type 
```
xrandr
```
which should output something like
```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 connected (normal left inverted right x axis y axis)
   1920x1200      60.0 +
   1600x1200      60.0
   1280x1024      75.0     60.0
   1280x960       60.0
   1152x864       75.0
   1024x768       75.1     70.1     60.0
   832x624        74.6
   800x600        72.2     75.0     60.3     56.2
   640x480        72.8     75.0     66.7     60.0
   720x400        70.1
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x600       60.0*+
   800x600        85.1     72.2     75.0     60.3     56.2
   640x480        85.0     72.8     75.0     59.9
   720x400        85.0
   640x400        85.1
   640x350        85.1
```
use the feedback to tailor the commands below
```
xrandr --output VGA1 --mode 1920x1200 --pos 0x0 --output LVDS1 --off
xrandr --output VGA1 --off --output LVDS1 --mode 1024x600 --pos 0x0
xrandr --output VGA1 --mode 1920x1200 --pos 0x0 --output LVDS1 --mode 1024x600 --pos 1920x600

```

---

