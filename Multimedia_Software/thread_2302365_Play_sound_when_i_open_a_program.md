---
title: "Play sound when i open a program"
date: 2015-11-09
forum: Multimedia Software
---

### Post by elemental2 on 2015-11-09
DISCLAIMER: I have no idea where to put this thread so I hope this is a good spot :3 Plz move it if its not.

Anyway so i switched to linux about a week ago. And im loving the customization. Im on Ubuntu with cinnamon desktop. I have nvidia drivers and a nvidia graphics card.

I would like it play a sound every time a program is opened. Is that possible?
Im mainly doing this to see just how customizable Linux is.

Thanks in advance.

---

### Post by tgalati4 on 2015-11-10
Right-click on the desktop, select Create Launcher.

In the Command box, put in your script:

```
play /usr/share/sounds/linuxmint-gdm.wav ; /usr/bin/pluma
```

I'm running MATE, so your sound files will be different, as well as your editor--probably *gedit*.

Welcome to the forums.

---

### Post by vasa1 on 2015-11-10
> **tgalati4 said:**
> Right-click on the desktop, select Create Launcher.

In the Command box, put in your script:

```
play /usr/share/sounds/linuxmint-gdm.wav ; /usr/bin/pluma
```

I'm running MATE, so your sound files will be different, as well as your editor--probably *gedit*.

Welcome to the forums.
Is that just "play" on MATE? I've seen mention of "aplay" and I use "mplayer -really-quiet" in my Openbox session.

---

### Post by Yellow Pasque on 2015-11-10
'play' is a sox command:
```
dpkg-query -S /usr/bin/play
sox: /usr/bin/play
```

---

### Post by vasa1 on 2015-11-10
> **Temüjin said:**
> 'play' is a sox command:
```
dpkg-query -S /usr/bin/play
sox: /usr/bin/play
```
Thanks, for clarifying. I don't have sox installed.

---

### Post by tgalati4 on 2015-11-10
Yes, *play*, *aplay*, *mplayer*, should all work, depending on what you have installed.  Sorry for the confusion.

---

### Post by Yellow Pasque on 2015-11-10
Don't forget paplay and canberra-gtk-play..

---

