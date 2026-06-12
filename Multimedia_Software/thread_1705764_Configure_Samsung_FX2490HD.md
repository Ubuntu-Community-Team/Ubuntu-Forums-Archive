---
title: "Configure Samsung FX2490HD"
date: 2011-03-12
forum: Multimedia Software
---

### Post by fabio.montefuscolo on 2011-03-12
I'm trying to configure my display on Ubuntu, but I'm getting problems to define the screen resolution. The native resolution for FX2490HD is 1920x1080, but Ubuntu only recognizes 1360x768.

Following a recipe[1] that uses xrandr I can setup 1920x1080, but the image looks strange. In this mode, I see shadows behind the blurred letters.

This is the code that I typed to follow the recipe:
```

cvt 1920 1080 60
xrandr --newmode "1920x1080_60.00" 173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00
xrandr --output VGA1 --mode 1920x1080_60.00

```

[1] [http://askubuntu.com/questions/19954/how-to-set-the-monitor-to-its-native-resolution-which-is-not-listed-in-the-resolu](http://askubuntu.com/questions/19954/how-to-set-the-monitor-to-its-native-resolution-which-is-not-listed-in-the-resolu)

Any help is welcome,
cheers,

---

### Post by fabio.montefuscolo on 2011-03-14
I got a better image with the code below.

```

xrandr --newmode "1920x1080_60.00" 148.35 1920 2008 2052 2200 1080 1084 1089 1125 +hsync +vsync
xrandr --addmode VGA1 1920x1080_60.00

```

But the image continues ugly. I think it's time to pray...

---

### Post by fabio.montefuscolo on 2011-03-17
Sorry for this thread. But my problem was a bad VGA cable. I bought a new one and now Ubuntu recognized my display as Samsung FX2490HD.

:popcorn:

---

