---
title: "how to completely clean out and reinstall audio server"
date: 2009-05-08
forum: Multimedia Software
---

### Post by Kain000 on 2009-05-08
hey everyone, 

So what started out as a problem with my digital audio output is now offically a complete sound problem, no sound from even the headphone jack.  I dont know what caused it to start or become this bad BUT i just want to fix it.   

Thought about a complete re-install but that seems too aggressive, how can I just wipe out and then re-install my audio drivers?

---

### Post by Kain000 on 2009-05-08
oh and im pretty sure i was using the ALSA modules to control my built in SPDIF digital audio port. any way to just reset those to say the settings of a fresh install?

---

### Post by Kain000 on 2009-05-09
BUMP!!  anyone??? this is really annoying and I just upgraded to jaunty, no help.   confirm that hardware works in vista so it's def a problem with ubuntu.   

how can i reinstall the module?????

---

### Post by markbuntu on 2009-05-09
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

---

### Post by Kain000 on 2009-05-10
> **markbuntu said:**
> (1) Remove the ALSA packages. From a terminal:
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

thanks so much for the reply, your my hero!!!

---

