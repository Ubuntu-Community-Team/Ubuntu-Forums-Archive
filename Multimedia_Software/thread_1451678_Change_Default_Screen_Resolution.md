---
title: "Change Default Screen Resolution"
date: 2010-04-10
forum: Multimedia Software
---

### Post by Alt-A on 2010-04-10
I have an Evga 275 video card and I have the nvidia x server on administration, every time I start up the resolution is auto.  I want it to be 1200x800 I have tried an xrandr command but that does not seem to work.  I have an HDMI connection.

---

### Post by Alt-A on 2010-04-14
Please Help.

---

### Post by WinterRain on 2010-04-14
Do:
```
gksudo nvidia-settings
```
and make your changes there. Then hit **apply**, then **save to X configuration file**.

---

### Post by Alt-A on 2010-04-14
I have tried that this is what i get.

---

### Post by WinterRain on 2010-04-14
OK. Just do:
```
sudo rm /etc/X11/xorg.conf
```

```
gksudo nvidia-settings
```
again, make your changes, apply, save to x, and it will see you don't have a xorg.conf file. Hit the button **show output**, and copy the contents to a new xorg.conf file. Make a new xorg.conf by ```
sudo touch /etc/X11/xorg.conf
``` then ```
gksudo gedit /etc/X11/xorg.conf
``` and copy over the contents.  It sounds strange, but it works. Leave nvidia-settings open while copying to your blank xorg file.

---

