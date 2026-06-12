---
title: "CPU almost at full capacity with light 3D animation running"
date: 2008-08-18
forum: Multimedia Software
---

### Post by asdir on 2008-08-18
The CPU is a 2.2 GHz Pentium 4, the graphics card is an nvidia GeForce3 TI-200. (1 GB RAM)

Whenever I start Diablo II the CPU is at almost 100% load, so the game laggs most of the time. That did not happen under Windows. I already suspected that it is the graphic card's fault and followed the advice here:
[http://ubuntuforums.org/showthread.php?t=889884](http://ubuntuforums.org/showthread.php?t=889884)

Does anyone here have any good ideas?

---

### Post by ibuclaw on 2008-08-18
Are you using "top" to show the CPU activity?

If not, use it.

There is a bug in the Gnome-System-Monitor that simply causes the app to use an anomalous amount of CPU. So your readings might be wrong.

As for the game, which OS is it native to?

[EDIT]
Define "light 3D animation"...?
Compiz and Gnome can do some hefty things on a system that is already pretty loaded. Perhaps that is the problem, and you shoudl try turning compiz off before you play.
```
metacity --replace &
```

Regards
Iain

---

### Post by asdir on 2008-08-18
Yes, I use top and the system monitor (which gets its info from top, I guess)

Since the game laggs I think the readings are correct.

Diablo II is a native Windows game but I have seen and played it on many other PCs with Linux/Wine, one actually almost the same built as mine (same CPU, slower graphics card, half as much RAM).

That compiz-replacement did not work, but still thanks for the effort. Any more advice?

---

