---
title: "Compiz failing to start"
date: 2011-01-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2011-01-18
On the latest updates I am getting an intermittent message at startup which informs me that the system is dropping to 2D mode. Sometimes this does not happen but the system still drops from 3D to 2D., wobbly windows disappear etc.

Restarting Compiz in a terminal (Compiz --replace) works and the system runs normally. I have looked in dmesg and syslog but can find no Compiz related error.

This is on a Samsung N150 netbook

Anyone else getting this flavour of error :-)

---

### Post by dino99 on 2011-01-18
Looks like the graphic card cant provide enough frames when requested, maybe a too high rate for the available graphic ram

---

### Post by Peter09 on 2011-01-18
Well it proved an intermittent problem. Seems to ocassionally happen with the nm-applet as well. Again, running it from a terminal is fine, with no problems.

---

