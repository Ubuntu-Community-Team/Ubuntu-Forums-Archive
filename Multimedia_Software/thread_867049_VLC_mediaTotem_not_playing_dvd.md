---
title: "VLC media/Totem not playing dvd"
date: 2008-07-22
forum: Multimedia Software
---

### Post by grayfox444 on 2008-07-22
This is an odd problem I've just started having, I'm not sure what would have caused it.
When I put in a DVD and open it with totem it says the source is unreadable, and when I open it in VLC media player it just closes immediately.
Any ideas?

---

### Post by grayfox444 on 2008-07-22
this happened after an automatic update install, has this happened to anyone else?

---

### Post by LazyEngineer on 2008-09-27
I'm having a similar problem.  Followed several different guides on how to get the right codec's etc, and can't get DVD's to play right to save my life.  At best, I get a garbled mess.  Most of the time the players just crash out, give error messages, or otherwise won't play.

Using Ubuntu Hardy (latest version as of today)

I've tried Totem, MPlayer, VLC.  No joy.

---

### Post by wolfen69 on 2008-09-27
let's try removing and reinstalling a couple things.
```
sudo apt-get purge libdvdread
```
```
sudo apt-get purge libdvdcss2
```
```
sudo apt-get clean
```
```
sudo apt-get autoremove
```
```
sudo apt-get install libdvdread libdvdcss2
```

---

