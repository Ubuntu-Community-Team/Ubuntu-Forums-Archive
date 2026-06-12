---
title: "Increase VGA Port resolution"
date: 2010-07-26
forum: Multimedia Software
---

### Post by jalberro on 2010-07-26
Hi, I have a question.
How can I increase the resolutions of my VGA Port?
As you can see in the screenshot, the maximum resolution that Ubuntu 10.04 detect it's 1360x768 but in other OS I can use 1920x1080 for example.

[IMG]http://img831.imageshack.us/img831/8308/stiscreenshotf.png[/IMG]

Thanks in advanced!

---

### Post by Bachstelze on 2010-07-26
xrandr is mostly obsolete.  What's your graphics card?

---

### Post by jalberro on 2010-07-26
Bachstelze, that's my VGA card.

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

I'm using Ubuntu in a HP Pavilion.

---

### Post by Bachstelze on 2010-07-26
With Intel cards, you sometimes still have to put your desired resolution in xorg.conf.  Normally, you don't have one by default in Ubuntu, you can generate one with

```
sudo X -configure
```

The file will be created as xorg.conf.new, at the bottom you will have something like this:

```
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection

```

Change it to

```
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes     1920x1080
        EndSubSection

```

SAve the file, copy it to /etc/X11/xorg.conf and restart X.

---

### Post by jalberro on 2010-07-26
I don't know but I can't configure the VGA resolution in that way, It doesn't work.

I solve using xrandr:

```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00

```And after that edit the /etc/gdm/Init/Default and put those lines. I don't know it this is the best way but it's works!

Thanks Bachstelze for your help! :D

---

