---
title: "monitors not detected correctly... stuck at 1360x768"
date: 2010-06-09
forum: Multimedia Software
---

### Post by FreezWay on 2010-06-09
I had a working 10.04 installation and everything was good, then i compiled my own kernel and screwed things up. So I reinstalled and installed my graphics drivers. But Ubuntu can't seem to get my correct resolution. So I am stuck at 1360x768... My monitor is 1920x1080.

Here are some relevant files:
/etc/X11/xorg.conf: [http://pastebin.com/FM6jC1rX](http://pastebin.com/FM6jC1rX)

/var/log/xorg.0/log: [http://pastebin.com/cbdjmX2g](http://pastebin.com/cbdjmX2g)

I have tried the instructions [here.]("http://https://wiki.ubuntu.com/X/Troubleshooting/Resolution#Problem:%20%20Wrong%20resolutions,%20refresh%20rates,%20or%20monitor%20specs") 

All help appreciated.... this resolution is giving me a headache.

---

### Post by efflandt on 2010-06-10
How is your monitor connected?  DVI is often digital and analog (with VGA adapter) and it may be confused.  Try adding this to the Screen section of xorg.conf (I guess for Digital Flat Panel):

Option "UseDisplayDevice" "DFP"

I am not that familiar with nVidia except an old laptop that got no screen at all with nVidia driver until I tried that, and not sure what else you tampered with.

---

### Post by FreezWay on 2010-06-10
heres how its connected 

gfx card has a dvi, then i put a dvi to vga converter, then vga cable then monitor.

---

### Post by efflandt on 2010-06-10
For some reason Linux is usually unable to determine proper video modes for VGA, so it uses a list of its own standard modes.  I am using DVI to HDMI cable on a 1080p HDTV and my PC automatically recognizes it as 1920x1080.

But if I connect a laptop with VGA, it does not list that mode and actually defaults to 1024x768, which it figures both the laptop display and external display should be able to handle (laptop display is actually 1280x800 if booted without external monitor).

But using xrandr commands, I am able to turn off the laptop display and set laptop VGA to 1920x1080, which works great.  I actually put those commands in a shell script so I can double click a launcher on my laptop desktop to do that when connected to the external display.

See what xrandr in a terminal shows for your active video device.  I am guessing that it is CRT-0 from your Xorg.0.log.  The following suggested commands to test how this works are based on a modeline I got from Xorg.0.log of the DVI to HDMI connected desktop PC.  If xrandr shows you active video device to be something other than CRT-0 substitute that instead below (scroll over if necessary to see all of modeline):

```
xrandr --newmode "1920x1080_60.00"  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync
xrandr --addmode CRT-0 1920x1080_60.00
xrandr --output CRT-0 --mode 1920x1080_60.00
```Note that xrandr commands are temporary, so if you log out of X and log back in, those settings would be cleared.  If that does not work, is the wrong size, or does not sync with your monitor, try the modelines from **cvt 1920 1080 60** or **gtf 1920 1080 60**.

If/when you find a modeline that works, this explains how to plug that into xorg.conf [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by FreezWay on 2010-06-13
xrandr: cannot find output "CRT-0"

on the 2nd command


warning: output CRT-0 not found; ignoring

on the 3rd

---

### Post by Bif Powell on 2010-08-12
I get the following with xrandr and xrandr -q


Screen 0: minimum 2688 x 1152, current 2688 x 1152, maximum 2688 x 1152
default connected 2688x1152+0+0 0mm x 0mm
   2688x1152      50.0* 


I think I know what to type, but I don't know what names to use for the displays in xrandr's commands

DFP DFP1 DFP-1 HDMI HDMI-1 HDMI1

all come back as: 

warning: output HDMI-0 not found; ignoring
warning: output HDMI-0 not found; ignoring
warning: output HDMI-1 not found; ignoring

I found a script here that I modified below: [https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor](https://help.ubuntu.com/community/BinaryDriverHowto/DynamicMultiMonitor)


```
#!/bin/sh

# Sets the secondary display to the proper resolution if attached.

LEFT="HDMI1"
RIGHT="HDMI0"

xrandr --output $RIGHT --preferred

xrandr --output $RIGHT --mode "2048x1152" --pos 1680x0 --primary --output $LEFT --mode "1680x1050" --pos 0x500
```

---

