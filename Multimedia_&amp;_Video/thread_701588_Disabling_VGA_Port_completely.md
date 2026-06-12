---
title: "Disabling VGA Port completely"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by halflife28 on 2008-02-19
I have an Acer x243w monitor, I don't know why the BIOS and start up screens do not show up on the DVI port of my video card. But anyway, I have this monitor plugged into both the VGA and DVI port of my ATI x700 Pro AGP card, that's the way I have to have it if I want to see the startup messages. Ubuntu boots up with a low resolution on the VGA side, and 1920x1200 on the DVI side with all the Gnome panels constrained to the size of the VGA and it flickers like crazy.

Is there anyway I can disable this VGA port without me plugging it in and unplugging it every time I boot?

---

### Post by halflife28 on 2008-02-19
On a side note, what I would want it to do exactly just like I have it set up when I dual boot Windows XP is start off in analog mode then switch over to DVI when X starts up.

Any help would be greatly appreciated.

---

### Post by halflife28 on 2008-02-19
Ok, I figured out how to do it with xrandr but how do I save this confiuration?

I used the commands to fix my problem to exactly how I want it:

```
xrandr --output DVI-0 --refresh 60
xrandr --output VGA-0 --off
```

---

### Post by disturbedite on 2008-02-19
i'd recommend a higher refresh rate if possible, 60Hz isn't easy on the eyes...

---

### Post by halflife28 on 2008-02-19
It's an LCD monitor, 60hz is the highest it goes on 1920x1200 and that's all the open source radeon driver supports anyways.

---

### Post by disturbedite on 2008-02-20
that sucks, oh well.

---

### Post by halflife28 on 2008-02-20
I figured out my problem. I have noticed a few who experienced this rare scenario. So I will state what I did to solve.

Add this line under the Device section in your xorg.conf file:
```
Option "monitor-VGA-0" "VGAConnection"
```

Then create a simple monitor:
```
Section "Monitor"
Identifier "VGAConnection"
Option "Disable" "True"
EndSection
```

Your second virtual desktop probably got disabled, to remedy this, refer to this:
[http://ubuntuforums.org/showthread.php?t=574713]("http://ubuntuforums.org/showthread.php?t=574713")

---

