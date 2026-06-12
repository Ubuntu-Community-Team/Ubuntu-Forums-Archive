---
title: "How do you remove sound files?"
date: 2011-10-30
forum: Multimedia Software
---

### Post by pepsifx357 on 2011-10-30
How can I delete ALL of the default Ubuntu sound files from my machine?

I'm using ALSA, and I'm tired of trying to quit firefox, only to be BLASTED out of my chair by the Ubuntu drum roll asking me if I want to close all of the tabs.  It scares me every time.  I can't use the "sound" options to turn them off.  So I need to delete them.  Where can I find the files?

Thanks,

Ben

---

### Post by WasMeHere on 2011-10-30
Hi Ben,

Before deleting them, maybe someone can help you switch the sound effects off. It will be easier to help, if you tell us what flavour and version of Ubuntu that you are running.

Have fun finding out :-)
Olle

---

### Post by pepsifx357 on 2011-10-31
I've got Ubuntu Desktop 10.04.  I've removed everything pulse audio and have installed everything ALSA for my studio.

---

### Post by WasMeHere on 2011-10-31
So you can't switch off the sound effects using the
**[FONT="Courier New"][SIZE="3"]gnome-volume-control[/SIZE][/FONT]** GUI?
I have it in Swedish (but it should something like 'audio effects', 'activate sounds for windows and buttons' and 'alarm volume').

Could it be that the GUI assumes that you run pulse-audio, and you would need another tool (or a terminal command) to do it for ALSA?

---

### Post by tartalo on 2011-10-31
```
sudo apt-get remove ubuntu-sounds
```
I hate them too.

---

### Post by pepsifx357 on 2011-11-01
> **tartalo said:**
> ```
sudo apt-get remove ubuntu-sounds
```
I hate them too.

Awesome!  Thanks!

---

