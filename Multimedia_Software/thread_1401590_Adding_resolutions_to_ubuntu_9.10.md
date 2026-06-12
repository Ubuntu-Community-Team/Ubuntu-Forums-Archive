---
title: "Adding resolutions to ubuntu 9.10"
date: 2010-02-08
forum: Multimedia Software
---

### Post by ledererster on 2010-02-08
I'm trying to add a higher resolution to my system.  I've tried to edit xorg.conf but i think i'm wrong.  Everytime I edit and reboot, it tells me I need to run in low graphics mode for now.  Now I'm trying 'xrandr.' I was able to create a new mode just fine, but when I try to add it to the appropriate output, i get this: 
```
prog@ubuntu:~$ xrandr --addmode LVDS1 1280x1024_50.00 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

```

here's what xrandr returns:

```
prog@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 286mm x 214mm
   1024x768       60.0*+   50.0  
   800x600        60.3     56.2  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)
  1280x1024 (0x111)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz
  1280x1024_50.00 (0x112)   89.4MHz
        h: width  1280 start 1352 end 1488 total 1696 skew    0 clock   52.7KHz
        v: height 1024 start 1025 end 1028 total 1054           clock   50.0Hz

```

I don't know why it puts it in TV1. There's two of them because I tried two different refresh rates.

Thanks in advance!

---

### Post by janidotux on 2010-02-08
Have you tried Display menu? System -> Preferences -> Display. This allows you to change your display settings.

---

### Post by Cabs21 on 2010-02-08
You might be limited to a maximum resolution by A. your graphics card or B) your screen.  Certain screens can not display above a certain resolution due to physical limitations.  The graphics card can not display higher resolutions possibly because your drivers are not up to date or installed.  what type of screen are you using and what graphics card?

---

### Post by efflandt on 2010-02-08
What is the native resolution of your laptop display (ie, LSVD1)?  286mm x 214mm appears to be a small display.  What makes you think that it is capable or 1280x1024?

If you are trying to connect an external VGA monitor, try booting with the monitor on with VGA input selected.  And then try setting the mode for VGA1.  But 50 Hz is an odd frequency.

You did not show output from **cvt 1280 1024**.

---

