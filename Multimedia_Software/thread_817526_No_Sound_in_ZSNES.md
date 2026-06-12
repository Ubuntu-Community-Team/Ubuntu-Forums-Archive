---
title: "No Sound in ZSNES"
date: 2008-06-03
forum: Multimedia Software
---

### Post by Anti-Tedd on 2008-06-03
I'm using Hardy 8.04 and I have an Intel ICH5 sound card that works perfectly in everything but ZSNES. I've messed with the sound options in the program but to no avail. Running it as root doesn't help either. Can someone please help me?

---

### Post by DaveKong on 2008-06-04
Try typing "zsnes --help" in the terminal to see options for sound. I had to switch my settings to sdl to get my sound to work. You may need to try different settings to get better sound quality.

```
zsnes -ad sdl
```

---

### Post by Tinker Dragoon on 2008-06-06
In my experience, sdl sound is the only setting that works for zsnes, but you also need to have specific sdl audio libraries installed. In Kubuntu Hardy, libsdl1.2debian-oss is the only one that gives me decent sound; the other flavors (libsdl1.2debian-all, -alsa, -pulseaudio, etc.) give me either no sound or extremely scratchy sound. In Ubuntu Hardy, libsdl1.2debian-esd was the only one I had success with, oddly enough. 

Others' experience may differ.

---

### Post by Heggerud on 2008-06-08
try my guide to get libao working
[http://ubuntuforums.org/showthread.php?p=5136009#post5136009](http://ubuntuforums.org/showthread.php?p=5136009#post5136009)

---

