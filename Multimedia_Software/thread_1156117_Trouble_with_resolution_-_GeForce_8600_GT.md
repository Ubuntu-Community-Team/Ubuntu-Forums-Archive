---
title: "Trouble with resolution - GeForce 8600 GT"
date: 2009-05-11
forum: Multimedia Software
---

### Post by Master Planeswalker on 2009-05-11
Hello,

a few days after upgrading my Ubuntu installation to 9.04, my screen resolution got down from 1280x1024 to 1024x768, without apparent reason.

I'm using a nVidia GeForce 8600GT on a 14'' TFT display, native res. 1280x1024.

I tried reinstalling the drivers (I'm using the ver. 180 nVidia drivers) several times, to no use.

I've also tried the steps on [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution"), but I get an error:

```

alberto@ubuntu:~$ cvt 1280 1024 75.0
# 1280x1024 74.90 Hz (CVT 1.31M4) hsync: 80.30 kHz; pclk: 138.75 MHz
Modeline "1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync
alberto@ubuntu:~$ xrandr --newmode "1280x1024_75.00"  138.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync 
alberto@ubuntu:~$ xrandr
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
  1280x1024_75.00 (0x165)  138.8MHz
        h: width  1280 start 1368 end 1504 total 1728 skew    0 clock   80.3KHz
        v: height 1024 start 1027 end 1034 total 1072           clock   74.9Hz
alberto@ubuntu:~$ xrandr --addmode default 1280x1024_75.00
alberto@ubuntu:~$ xrandr
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1280 x 1024
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   512x384        57.0  
   400x300        58.0  
   320x240        59.0  
   1280x1024_75.00   74.9  
alberto@ubuntu:~$ xrandr --output default --mode 1280x1024_75.00
xrandr: Configure crtc 0 failed

```

I'm at a loss for solutions, even more since this happened suddenly. Everything else is working just fine. Any help would be greatly appreciated. Thanks in advance.

---

### Post by desconocido on 2009-05-13
I had a similar problem. My laptop suddenly defaulted to a lower resolution (800 x 600), but then started working again properly, and then failed again more permanently. So I assumed it was a hardware problem.

However, booting from the install CDROM worked, as did installing a second version on a new partition of the hard disk.

So I assumed this was something I could fix and started reading these forum threads.

I got the same "xrandr: Configure crtc 0 failed" error.

However, sloppily, when I rebooted, I chose one of the the other boot options from the long list I was now offered. Can't remember the name but it had something like "(Rescue version)" after the description of the kernel version etc. This passed me to screen with a menu of about three items, and I chose one with a title something like "Let X.conf try and discover your screen resolutuion". After that everything worked fine again with 1280 x 800 resolution!

Maybe there is an intermittent fault with the hardware telling Ubuntu what resolutions it has and X gets itself in a twist when that happens?

```
$lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```

---

