---
title: "How to switch display between laptop and external monitor."
date: 2010-05-02
forum: Multimedia Software
---

### Post by parsh78 on 2010-05-02
With help from this article [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2), I have created two scripts. 

1 LaptopScreen.sh
Executing this script turns off external monitor attached to laptop and turns on laptop LCD. You may change the value of "1024x600" to the one your laptop supports.
```

xrandr
xrandr --output LVDS1 --mode 1024x600 --primary --output VGA1 --off

```

2 ExternalMonitor.sh
This script turns off laptop monitor and diverts display to external LCD. My monitor supports 1920x1080, you can replace it with optimum resolution of your monitor.
```

xrandr
xrandr --output VGA1 --mode 1920x1080 --primary --output LVDS1 --off

```

This can be further automated by assigning key shortcuts.

This is my first contribution to UbuntuForums, let me know your comments or suggestions

---

### Post by K.Mandla on 2010-05-02
Moved to Multimedia and Video. :)

---

