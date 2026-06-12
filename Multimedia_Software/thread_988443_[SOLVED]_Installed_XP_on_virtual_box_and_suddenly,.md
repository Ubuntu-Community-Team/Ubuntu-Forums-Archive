---
title: "[SOLVED] Installed XP on virtual box and suddenly, no sound"
date: 2008-11-20
forum: Multimedia Software
---

### Post by addict[B] on 2008-11-20
Hi,

I'm running Hardy on my laptop and the other day I installed virtual box so I could run XP if I needed to. I finally got round to installing XP on Vbox yesterday and now my laptop won't produce a sound, not even a command line beep. I've been running ubuntu since feisty and never had any problems before.

I have a feeling it was to do with me installing the hardware drivers for my laptop in the vbox XP. I removed the XP drivers from vbox and tried [this]("http://ubuntuforums.org/showthread.php?t=205449") but all to no avail. My soundcard is an ATI IXP SB400 AC'97, when I run
```
aplay -l
```
I get
```
aplay: device_list:205: no soundcards found...
```

Cheers for any help.

Ben

---

### Post by stinger30au on 2008-11-20
i have the same dramas with 8.10 with xp in virtual box

im not worried about it, sound is the least of my dramas though

a fix would be nice though

---

### Post by addict[B] on 2008-11-20
It's good to know I'm not the only one :)

---

### Post by addict[B] on 2008-12-19
upgrading to intrepid ibex solved this problem, not the best solution but it worked :)

---

