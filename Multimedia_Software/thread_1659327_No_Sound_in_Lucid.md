---
title: "No Sound in Lucid"
date: 2011-01-03
forum: Multimedia Software
---

### Post by 36000 on 2011-01-03
Hello, everyone. I'm a new user of Ubuntu. I've just installed ubuntu 10.04(lucid) on my notebook side by side with win 7, but after installation i got no sound, even when startup. Does anybody have a solution on my case?

---

### Post by lidex on 2011-01-04
First thing to do is check your levels in alsamixer/gnome-alsamixer.
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

