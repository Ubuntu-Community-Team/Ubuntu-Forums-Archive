---
title: "OSS and Kmix"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Shardsofmetal on 2008-07-19
I installed OSS on my laptop because it has an ich8 chipset, which is not supported by ALSA. I was wondering if anybody has found an easy way to get Kmix to work with OSS (without me having to recompile) or if there are any other mixers that work for KDE. All I want is something that sits in the KDE tray that controls the main volume, that can also be controlled by the volume up/down buttons on my laptop. If anybody knows of a way I can achieve this, I will be very happy. I know that it works in GNOME, but I need something that works in KDE. I don't want to have to open ossxmix just to make a minor adjustment to the volume. Thank you

---

### Post by Creative2 on 2008-07-19
I have written here about what i do to increase my mic volume

[http://fuocotools.byethost13.com/index.php?topic=149.0](http://fuocotools.byethost13.com/index.php?topic=149.0)

```
kdesudo systemsettings
```

--->Sound System
------>Hardware
-------->Select Device (remember the default should be Autodetect)
--------->Opend Sound System

close
[B]
open kmix[/B]
------>Settings
------->Configure KMix
-------->set un-checkek Restore Volumes on log in

----------> Now set your volumes on kmix

```
kdesudo systemsettings

```
--->Sound System
------>Hardware
-------->Select Device
--------->Set Autedetect or what you had before

close

---

### Post by Shardsofmetal on 2008-07-19
That didn't fix the problem. I uninstalled ALSA when I installed OSS 4.0. Now, Kmix doesn't have any mixers to select in the settings window.

---

### Post by Creative2 on 2008-07-19
then try thsi

[http://docs.kde.org/stable/en/kdemultimedia/kmix/tips-and-tricks.html#id2545838](http://docs.kde.org/stable/en/kdemultimedia/kmix/tips-and-tricks.html#id2545838)

---

### Post by Shardsofmetal on 2008-07-19
I already had that enabled (I saw that suggestion somewhere else before). Is there any way to use the gnome volume control in kde? That works with OSS.

---

### Post by Shardsofmetal on 2008-07-20
Anybody have any ideas?

---

