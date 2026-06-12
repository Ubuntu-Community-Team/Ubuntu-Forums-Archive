---
title: "Sound being too quiet after upgrade to 10.4"
date: 2010-05-19
forum: Multimedia Software
---

### Post by duksis on 2010-05-19
Hi,

I'm having an issue with my headphones - they work but they are so quiet  that I can barely hear something.
I use jabra GN 2000 USB OC headphones and the sound before upgrading to 10.4  was ok.

Any suggestion on what could be the cause?

---

### Post by lidex on 2010-05-20
Try your mixers. 
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

No help? Need some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Also helpful is the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by duksis on 2010-05-21
Lidex thank you very much!! 
Alsamixer from terminal did the trick for me.

---

