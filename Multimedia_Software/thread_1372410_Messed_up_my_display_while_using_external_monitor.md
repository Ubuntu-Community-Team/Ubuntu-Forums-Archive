---
title: "Messed up my display while using external monitor"
date: 2010-01-04
forum: Multimedia Software
---

### Post by Udibuntu on 2010-01-04
Hi All,

I'm using Karmic on an Acer 751.

While connecting via VGA to an HDTV I clicked OK on the "display" menu and messed up my resolution on the Acer.

Is there a way to restore the monitor settings to their original state? All I'm getting under "display" menu is an "unknown" screen instead of "default" screen with lower resolution (1024X768) instead of 1366X768.

Please help!!

---

### Post by Hydrosis on 2010-01-04
> **Udibuntu said:**
> Hi All,

I'm using Karmic on an Acer 751.

While connecting via VGA to an HDTV I clicked OK on the "display" menu and messed up my resolution on the Acer.

Is there a way to restore the monitor settings to their original state? All I'm getting under "display" menu is an "unknown" screen instead of "default" screen with lower resolution (1024X768) instead of 1366X768.

Please help!!

I'm having a similar problem, but for different reasons.  This is what I have to do.

```

 1. Use xrandr to make sure that the new mode can fit within the maximum framebuffer size
      Code:

      xrandr | grep maximum

   2. Use gtf to create a mode line
      Code:

      gtf 1680 1050 59.9

   3. Add new mode using xrandr
      Code:

      xrandr --newmode "1680x1050_59.90"  146.89  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

   4. Add this newly added mode to the desired output (VGA/LVDS etc)
      Code:

      xrandr --addmode VGA1 1680x1050_59.90

   5. Choose the new mode
      Code:

      xrandr --output VGA1 --mode 1680x1050_59.90



```

After I log into Ubuntu, I click on an executable version of the script.

Below is the source for mine, which gives me a resolution of 1920x1200 at a frame rate of 59.9.  

Change the numbers to match your results accordingly.

```

#! /bin/bash 

xrandr | grep maximum &
sleep 2 
gtf 1920 1200 59.9 &
sleep 2 
xrandr --newmode "1920x1200_59.90"  192.83  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync &
sleep 2 
xrandr --addmode VGA1 1920x1200_59.90 &
sleep 2 
xrandr --output VGA1 --mode 1920x1200_59.90 &
exit 0


```

Save the file without an extension (not .txt) and then right click on the file and enable executing it as a program.  Then you simply double click the file, wait 6 or 7 seconds and your resolution problem will be fixed until you restart X or your computer.

I hope this helps.  It was driving me crazy, and still is.  My Windows XP partition works fine on this hardware, but Ubuntu not so much.

---

### Post by Udibuntu on 2010-01-05
```
udi@udi-netbook:~$ xrandr -q
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
udi@udi-netbook:~$ 

```

How can I change this back to 1366x768?

---

### Post by Udibuntu on 2010-01-06
Bump. Is there a way to restore xrandr so is recognizes lvds, vga etc? I dont get anything besides screen 0...

Help,please

---

### Post by Udibuntu on 2010-01-07
Well then, apparently GMA500 psb driver for Linux does not enable, or at least makes it harder, to alter settings in xrandr (both commandline and GUI).

Solution was to purge, remove and reinstall the psb driver. So far it is persistent, but I'm yet to try and plug an external screen again... I will update if I run into problems.

This is Udi signing off this thread, hopefully...

---

