---
title: "Sound problem on  ASUS P5GPL-X SE"
date: 2010-05-21
forum: Multimedia Software
---

### Post by reablaz on 2010-05-21
I have built-in audio card on my motherboard Asus P5GPL-X SE, system found it and it looks pretty ok. But when i'm listening any sound, there is terrible noise, like over-volumed. Nothing in driver manager found, i have no idea how to fix it.

I'm using Ubuntu desktop 10.04.

Any suggestions? Thank you.

---

### Post by lidex on 2010-05-21
Check for levels in your mixers.
**Alsamixer**
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
Use 'Edit -> Sound Card Properties' menu to enable elements.
Soundcard tab to select / adjust levels.

---

### Post by reablaz on 2010-05-22
Thank you for your answer!

---

