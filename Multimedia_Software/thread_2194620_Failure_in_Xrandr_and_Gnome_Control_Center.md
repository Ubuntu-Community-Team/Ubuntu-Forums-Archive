---
title: "Failure in Xrandr and Gnome Control Center"
date: 2013-12-19
forum: Multimedia Software
---

### Post by eldavar on 2013-12-19
Good afternoon everybody! I'm having some weird stuff happen that I can't seem to fix, or even figure out what went wrong. I'm running a fresh install of 13.10 on a brand new hard drive and I have 2 Dell 1908FP monitors. I'm gonna give as much relevant info as I can so hopefully we can get things working properly!

Initially, the display settings identified both monitors and I was able to extend my desktop and use both screens without a problem. But, for some unknown reason, this hasn't worked for the past 2 days. Now the desktop is just cloned. Every time I click the Display icon in the System Settings, the window immediately closes and nothing happens. I tried launching the Display settings from a terminal with ```
gnome-control-center display
``` and this is the result:```
greg@greg-ubuntu:~$ gnome-control-center display

(gnome-control-center:18820): Gtk-WARNING **: GtkTable does not have a property called expand

(gnome-control-center:18820): Gtk-WARNING **: GtkTable does not have a property called fill

(gnome-control-center:18820): Gtk-WARNING **: GtkTable does not have a property called position
**
GnomeDesktop:ERROR:gnome-rr-config.c:663:gnome_rr_config_load_current: assertion failed: (gnome_rr_config_match (config, config))
Aborted (core dumped)
```I then decided to try using Xrandr. Here's that output:```
greg@greg-ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA-1 connected (normal left inverted right x axis y axis)
   1280x1024      60.0 +   75.0  
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
VGA-3 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)
  1280x1024 (0x68)  108.0MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock   64.0KHz
        v: height 1024 start 1025 end 1028 total 1066           clock   60.0Hz

```Note, I cut the paste short at the end because it was just a really long list of available resolutions.

Initially, both of my monitors were on, but cloned. I tried to achieve extended desktop with ```
xrandr --auto --output DVI-0 --mode 1280x1024 --right-of VGA-1
``` It did not work. All that happened was the DVI-0 monitor turned off. I tried again, this time telling Xrandr to put the VGA monitor to the left of DVI instead, but got the same result.
Then, I figured I'd try ArandR just to see how that might work out. It didn't work either, but the result was different. The DVI monitor shut off, but the screen got stretched out in a weird way. Here's a screenshot:
[IMG]https://lh6.googleusercontent.com/-b9qjSREdtAc/UrNQ8_b9TjI/AAAAAAAAE7A/zTGAIsurltg/w893-h357-no/Screenshot+from+2013-12-19+14%253A30%253A05.png[/IMG]
Now, here's a "normal" screenshot of the error from ArandR:
[IMG]https://lh6.googleusercontent.com/-QfZAm4FpDfk/UrNQ8uF-JiI/AAAAAAAAE64/e8AbLUs2KTA/w429-h242-no/Screenshot+from+2013-12-19+14%253A39%253A26.png[/IMG]
I can't help but think that these errors are all related somehow. I'm hoping that someone can shed some light on this and help me fix it. 

Thanks!

---

