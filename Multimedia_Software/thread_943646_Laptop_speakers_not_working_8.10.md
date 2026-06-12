---
title: "Laptop speakers not working 8.10"
date: 2008-10-10
forum: Multimedia Software
---

### Post by sesquipedalianman on 2008-10-10
New install Kubuntu 8.10 on Intel 6730b.  Headphones work fine, but the internal speakers give me no sound.  I've verified nothing is muted, and I know the speakers work (laptop shipped w/ XP).  Any advice would be appreciated.

---

### Post by sesquipedalianman on 2008-10-14
I found the fix.  I added options snd-hda-intel model=laptop to the end of the /etc/modprobe.d/alsa-base file.

---

### Post by Megakazbek on 2008-10-15
Thanks, sesquipedalianman!
This fixed the same problem for me too, on HP 6530b laptop.

---

