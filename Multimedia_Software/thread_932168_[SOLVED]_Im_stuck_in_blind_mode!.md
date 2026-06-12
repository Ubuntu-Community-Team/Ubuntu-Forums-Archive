---
title: "[SOLVED] Im stuck in blind mode!"
date: 2008-09-28
forum: Multimedia Software
---

### Post by laxor on 2008-09-28
I installed ATI drivers via Envy and everything went fine(though i have hd4850), and I i wanted to try out some options and when I clicked turn off display (or similar) my screen went off ,now I cant return it to default setting, I tried to boot into recovery mode,fix X server,and reinstall driver ,when I reboot after reinstalling it it happens again, I can log in blind ,I hear my login music playing and files loading, everything works except my display ,is it eraseable or modifiable? Please help me!
Im forced in using ugly gfx mode now, or windows!


Thank you very much if you can help me.

---

### Post by laxor on 2008-09-28
I hope someone can help me here, I was looking for the solution via google and nothing..

---

### Post by mindoms on 2008-09-28
Where did you click "turn off display"?
please post your /etc/X11/xorg.conf

---

### Post by laxor on 2008-09-28
> **mindoms said:**
> Where did you click "turn off display"?
please post your /etc/X11/xorg.conf

I clicked it in ATI control panel,but it was so quick and without any need for "apply" or "ok" button, need to reboot for xorg.conf,
brb

---

### Post by laxor on 2008-09-28
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"hr"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection


btw Im in recovered mode again,I should have 1440x900 on my SM940BW, but this mode gives 1280x1024,no acceleration,only basic visuals work,so installing driver 8-6 via Envy again will get me to blind mode again, what to do?

---

### Post by laxor on 2008-09-28
Here is my xorg folder

[http://img408.imageshack.us/my.php?image=screenshotts8.png](http://img408.imageshack.us/my.php?image=screenshotts8.png)

---

### Post by mindoms on 2008-09-28
well. i dont own an ati card, so i wont be much help.
i just googled a bit and found out that your card needs catalyst 8.7

try to find an howto to install them. 

somebody suggested
```
sudo aticonfig --initial --force
```
maby this can undo your "turn display off" click in some setting files.

how do you enter this "recovered mode"?

---

### Post by laxor on 2008-09-28
Well, it is a normal boot choice mode, just below first optin which is linux kernel... is this recovery, after choosing it I can fix X server, libraries,and other stuff,after fixing X i can proceed with booting into the system

---

### Post by laxor on 2008-09-28
I will try sudo aticonfig --initial --force now ,be right back.

---

### Post by laxor on 2008-09-28
It WORKS!

Installed 8.7, used your code and voila!

THANX!

---

