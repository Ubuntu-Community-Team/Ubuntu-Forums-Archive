---
title: "ATI artifacts problem"
date: 2010-09-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by trigeorgis on 2010-09-12
Hello fellow ubuntu'ers. I have upgraded to the latest 10.10 beta and as FGLRX drivers are not yet available I m using the FOSS drivers.

The problem is i am encountering artifacts on my screen, (even in TTY). I think i had the same problem in 10.04 until i have upgraded to fglrx.

The artifacts are very small thin white horizontal lines over the screen.

Anyone ever seen this again?

Thanks

---

### Post by gfarmerfr on 2010-09-12
If you have a spare screen try with it. If the lines stays it's most likely a graphic card memory problem (overheating ?) if not it's a screen problem. Either way I don't think it's a driver problem.
For your information I have the same problem : my 24" LCD has 2 white lines of pixels across the screen. In other words the LCD is screwed but I deal with it for the time being :)

---

### Post by trigeorgis on 2010-09-12
The other screen works fine but its def. not a screen problem as it works great in other OSs and worked great on 10.04 before the upgrade...

---

### Post by cariboo on 2010-09-12
Check if /etc/X11/xorg.conf has any Horizontal and Vertical refresh rates set, and if they are the proper values for your monitor.

---

### Post by gfarmerfr on 2010-09-13
Lucky you :)
I can see these 2 white lines in the bios, with VGA/DVI/HDMI adapter, with the opensource/fglrx driver, with ubuntu/win7 and even with another ATI graphic card :(

---

### Post by trigeorgis on 2010-09-13
The hor/vert refresh rate is the first thing that came to me, but it doesnt seem to be affected.

here is the xrandr output:

```

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  

```

---

