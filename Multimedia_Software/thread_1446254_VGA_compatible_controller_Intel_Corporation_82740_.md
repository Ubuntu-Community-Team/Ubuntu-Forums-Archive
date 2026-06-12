---
title: "VGA compatible controller: Intel Corporation 82740 (i740) AGP Graphics Accelerator (r"
date: 2010-04-03
forum: Multimedia Software
---

### Post by phillw on 2010-04-03
Hi,

I have an OP who cannot get the screen resolution up from 800x600 on a monitor.
with the alterations in xorg.conf (not being used any more) I'm a bit stuck.

Any ideas ?

he's over at #lubuntu if you have IRC, else post questions here.

Thanks,

Phill.

---

### Post by linoox on 2010-04-03
Lubuntu Lucid Beta installed on an Intel P3 450Mhz machine with 256 MB RAM. Video card is i740. 

I had done the following:
- updated ubuntu core and other dist packages
- installed xserver-xorg-video-i740_1.3.2-1_i386.deb

Output from xrandr:
```

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0 

```

ran 'cvt 1024 768'
```

# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

```

executed the following lines:
* xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
* xrandr --addmode default 1024x768_60.00
* xrandr --output default --mode 1024x768_60.00

Output
```

xrandr: Configure crtc 0 failed

```

Not working so far. Any help will be much appreciated. Thanks.

---

### Post by Mark Phelps on 2010-04-05
linoox:  Lucid is still in beta testing, so you should be posting your Lucid-related issues to the proper testing forum: Development & Programming, Lucid Lynx Testing.

Please don't tack on any more responses to this thread.  Go to the Lucid testing forum instead.

Thanks

---

