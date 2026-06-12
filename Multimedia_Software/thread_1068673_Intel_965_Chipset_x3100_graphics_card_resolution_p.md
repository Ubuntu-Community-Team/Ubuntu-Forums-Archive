---
title: "Intel 965 Chipset x3100 graphics card resolution problem 1280*1024"
date: 2009-02-13
forum: Multimedia Software
---

### Post by monuratci on 2009-02-13
I' m using Ubuntu 8.10. My computer is HP Compaq 6720s and   it has Intel 965 Chipset x3100 graphics card. I can see 1024*800 and 800*600 resolution modes. In normally I can see 1280*1024 resolution on Microsoft Vista. I can use Compiz but I can not change to 1280*1024 because its not exist on System/Administration/Screen Resolution.
Followings are some outputs about my system:
```

~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: Intel(r)GM965/PM965/GL960 Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)GM965/PM965/GL960 Graphics Controller Hardware Version 0.0
memory: 7616kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 4445
eisa: SEC4445
serial: 00000000
manufacture: 0 2007
input: analog signal.
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1280x800@59
monitorid: SAMSUNG
monitorid: LTN154X3-L01


~$ glxinfo | grep direct
direct rendering: Yes


```

---

### Post by overdrank on 2009-02-13
Hi and welcome, you may look at the [X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution") to help with this issue.

---

### Post by monuratci on 2009-02-13
In the following link(X/Config/Resolution) I have tried to write commands and results:
```

~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)


```

```

$ xrandr --output LVDS --mode 1280x1024
xrandr: cannot find mode 1280x1024


```

```

~$  xrandr --addmode LVDS 1280x1024
xrandr: cannot find mode "1280x1024"


```

```

~$ gtf 1280 1024 60 -v -x
 1: [H PIXELS RND]             :     1280.000000
 2: [V LINES RND]              :     1024.000000
 3: [V FIELD RATE RQD]         :       60.000000
 4: [TOP MARGIN (LINES)]       :        0.000000
 5: [BOT MARGIN (LINES)]       :        0.000000
 6: [INTERLACE]                :        0.000000
 7: [H PERIOD EST]             :       15.723577
 8: [V SYNC+BP]                :       35.000000
 9: [V BACK PORCH]             :       32.000000
10: [TOTAL V LINES]            :     1060.000000
11: [V FIELD RATE EST]         :       59.998829
12: [H PERIOD]                 :       15.723271
13: [V FIELD RATE]             :       60.000000
14: [V FRAME RATE]             :       60.000000
15: [LEFT MARGIN (PIXELS)]     :        0.000000
16: [RIGHT MARGIN (PIXELS)]    :        0.000000
17: [TOTAL ACTIVE PIXELS]      :     1280.000000
18: [IDEAL DUTY CYCLE]         :       25.283018
19: [H BLANK (PIXELS)]         :      432.000000
20: [TOTAL PIXELS]             :     1712.000000
21: [PIXEL FREQ]               :      108.883200
22: [H FREQ]                   :       63.600000
17: [H SYNC (PIXELS)]          :      136.000000
18: [H FRONT PORCH (PIXELS)]   :       80.000000
36: [V ODD FRONT PORCH(LINES)] :        1.000000

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync


```

```

~$ xrandr --newmode "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync


```

```

:~$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0xa1)  108.9MHz
        h: width  1280 start 1360 end 1496 total 1712 skew    0 clock   63.6KHz
        v: height 1024 start 1025 end 1028 total 1060           clock   60.0Hz


```


```

~$ xrandr --output LVDS --mode 1280x1024
xrandr: cannot find mode 1280x1024

```

I think I'm very closed but I cant find solution:)

---

### Post by densou on 2009-02-14
> **monuratci said:**
> I think I'm very closed but I cant find solution:)

did you add xrandr output to your xorg.conf ? :) otherwise it won't work !

How to:
[http://www.x.org/wiki/Projects/XRandR](http://www.x.org/wiki/Projects/XRandR)

---

### Post by COKEDUDE on 2010-10-27
> xrandr: cannot find mode 1024×768

I see a lot of people are having trouble with this. 

In Linux capitalization is VERY important. Here you guys did not capitalize your the "X" in your resolution. Once you capitalize your "X" you should be good. Here is an example of what worked for me. 

```
xrandr --output VGA1 --mode 1024x768 --rate 60
```

---

