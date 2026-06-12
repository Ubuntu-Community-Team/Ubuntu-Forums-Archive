---
title: "audio problems"
date: 2009-05-08
forum: Multimedia Software
---

### Post by georgemx on 2009-05-08
hi all im new user of ubuntu and i have a little problem i don't have sound in my pc but i have a method to make it work and i don't now why i have to do this wen i swich on my pc 

ok what i do...
in a terminal i tipe this

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

and this fix the problem but why how i make it work normal.

---

### Post by markbuntu on 2009-05-09
Try reinstalling alsa. It is most likely something went wrong with the autodetect function and made a bad default setting.


(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

Then you shoud go here to get everythign set up properly

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

