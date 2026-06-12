---
title: "How to override xorg auto config"
date: 2008-08-29
forum: Multimedia Software
---

### Post by laydros on 2008-08-29
I have had a lot of trouble with resolutions in newer versions of Ubuntu. After a while I figured out it has to do with the fact that Ubuntu now auto-detects the video hardware on every restart. My current xorg.conf is nothing like I have seen in the past or on other distros, it just lists "Configured Monitor" and "Configured Video Device." I typically have trouble when using a KVM, or when I had the wrong VGA cable plugged into my monitor. The cable didn't pass all of the information from the monitor to the video card, so the OS assumed that the highest possible video settings were SVGA.

A couple of searches have shown me that a lot of people run into trouble with this, but most of the help they get is people telling them to edit xorg.conf. Unfortunatly the settings they put in will get overridden by the auto-detect.

I know enough to get a base xorg.conf and tweak it to what I need, but I'm ignorant about the auto-detect stuff. Does anyone know how to tell Ubuntu to leave my video config alone, and just read whatever I have in xorg.conf?

---

### Post by overdrank on 2008-08-29
Hi and all I can offer is you can try the command ```
gksu displayconfig-gtk
```and try and adjust there. I use a KVM switch and have no issues. Along with the nvidia settings.

---

### Post by laydros on 2008-08-29
I think I tried that with the problem in the past, and it didn't seem to stick, but this time it worked. Thanks so much for the help.

---

### Post by Scunge on 2008-08-29
Please see the end posts of [http://ubuntuforums.org/showthread.php?t=816679](http://ubuntuforums.org/showthread.php?t=816679) for a similar problem which has as yet had no further replies, but the config command suggested above didn't help. Wondered if anyone had any other thoughts or things to try?

---

