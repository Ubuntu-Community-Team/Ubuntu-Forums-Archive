---
title: "xrandr won't let me increase screen resolution"
date: 2010-06-23
forum: Multimedia Software
---

### Post by azile19 on 2010-06-23
Hello!

I have been arguing with my acer aspire one laptop since I bought it in terms of the screen resolution and have never been able to solve the problem, although I seem to be getting close.  I just updated to 10.04 (the netbook remix).

I have been following the instructions for how to fix it [here]("http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html").  The result was this:

```

liz@Pippin:~$ cvt 1366 768
# 1368x768 59.88 Hz (CVT) hsync: 47.79 kHz; pclk: 85.25 MHz
Modeline "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
liz@Pippin:~$ xrandr -q
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
liz@Pippin:~$ sudo xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync
liz@Pippin:~$ xrandr
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
  1368x768_60.00 (0x64)   85.0MHz
        h: width  1368 start 1440 end 1576 total 1784 skew    0 clock   47.6KHz
        v: height  768 start  771 end  781 total  798           clock   59.7Hz
liz@Pippin:~$ xrandr --addmode default 1368x768_60.00
liz@Pippin:~$ xrandr --output default --mode 1368x768_60.00
xrandr: screen cannot be larger than 1024x768 (desired size 1368x768)

```Does anyone know how to change the available screen resolutions? I'd really love to actually be able to use linux on this netbook!

Thanks!

---

### Post by cbrunhaver on 2010-06-23
Which model of aspire one is it?  There are a number of models under the "aspire one" name.   

This might be a place to start:

[https://help.ubuntu.com/community/AspireOne/AO751h](https://help.ubuntu.com/community/AspireOne/AO751h)

---

### Post by azile19 on 2010-06-24
Thank you for the link.  That just confirmed what I've been guessing which is that I need to suck it up and reinstall real Ubuntu rather than trying to fix my UNR since it's probably largely the source of my problems.

---

### Post by cbrunhaver on 2010-06-24
No, it doesn't have anything to do with the UNR UI etc.  It is really an issue of Intel outsourcing the graphics solution for their GMA500 "poulsbo" chipset and then not supporting the driver for a long time but using it in some linux targeted hardware.  

It looks like things are getting sorted out now and I would recommend checking out this page as well (near the top of this forum).  [http://ubuntuforums.org/showthread.php?t=1229345&page=128](http://ubuntuforums.org/showthread.php?t=1229345&page=128)

---

