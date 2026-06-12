---
title: "xrandr translate output"
date: 2010-07-10
forum: Multimedia Software
---

### Post by wannabegeek on 2010-07-10
hi people,

I have not been able to figure out how to get xrandr to translate the output to the left (-x direction).

Res is set to 1360x768 but the 'picture' is offset to the right by about 10 pixels and there is a black bar of unused screen on the left. 
tried
```
xrandr --output VGA-0  --pos -5x0 
```nothing happened, no errors either... :-s

---

### Post by wannabegeek on 2010-07-10
bump

---

### Post by jywarren on 2012-02-02
I have the same problem. Is it because I'm trying to position my primary (and only) monitor? 

I'm running:

```
xrandr --output LVDS1 --newmode "1024x600_60.00"  48.96  1024 1064 1168 1312  600 601 604 622  -HSync +Vsync

xrandr --addmode LVDS1 1024x600_60.00

xrandr --output LVDS1 --mode 1024x600_60.00
```

then

```
xrandr --output LVDS1 --mode 1024x600_60.00 --pos 100x100
```

does not work.

---

