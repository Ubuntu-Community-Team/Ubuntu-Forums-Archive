---
title: "Resolution Woes (Samsung Monitor)"
date: 2011-08-27
forum: Multimedia Software
---

### Post by SharkBreeder on 2011-08-27
I have an intel graphics card, and for some reason Ubuntu (11.04) is not detecting my Samsung SyncMaster 940bW LCD Monitor (1440x900). When I go to Monitor settings to change my resolution, it's marked as "Monitor: Unknown." I can't access anything from the drop down menus. Does anyone know how I can get this to work?

---

### Post by realzippy on 2011-08-27
Syncmasters often have a bad [Edid]("http://en.wikipedia.org/wiki/Extended_display_identification_data").
Post output from 

```
xrandr -q
```

---

### Post by SharkBreeder on 2011-08-27
Results of xrandr -q:

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1440 x 900, current 1440 x 900, maximum 1440 x 900
default connected 1440x900+0+0 0mm x 0mm
   1440x900        0.0* 
```

---

### Post by realzippy on 2011-08-27
Which intel card?
post
```
lspci |grep VGA
```

...but,according to xrandr,you already run
1440x900.......

---

### Post by SharkBreeder on 2011-08-27
Intel card:
```
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset 
Integrated Graphics Device (rev 01)
```

---

### Post by realzippy on 2011-08-27
Just asked to make sure you were not running an I3/5/7 Intel CPU with integrated graphics,which you do not.

Anyway,as mentioned,your resolution seems to be correct.
If you want a lower resolution,this is possible from the terminal,
but I think you do not want this....?

---

### Post by SharkBreeder on 2011-08-27
> **realzippy said:**
> Just asked to make sure you were not running an I3/5/7 Intel CPU with integrated graphics,which you do not.

Anyway,as mentioned,your resolution seems to be correct.
If you want a lower resolution,this is possible from the terminal,
but I think you do not want this....?

 I mostly just wanted to know if I had the ability to switch resolutions, and that nothing was wrong with my system; or my monitor. Thanks for your help.

How do you go by switching resolutions from the terminal?

---

### Post by realzippy on 2011-08-27
There is nothing really wrong with your system,the graphics card/driver just cannot "see" the monitor specific data correctly.
This may be due to a corrupt edid file,a bug in the driver,or even the
monitor cable.
Important thing is that it recognizes the native resolution of your panel,so
your eyes don't hurt.  ;-)
To provide other resolutions,you had to use the xrandr tool also.
Check out the web for "xrandr" to get an idea...
But since 1440x900 works,you should spend your linux-time with something useful....eg. my signature.
Please set this thread as solved (ThreadTools)
Have fun!

---

