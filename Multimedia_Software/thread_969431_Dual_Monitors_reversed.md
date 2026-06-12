---
title: "Dual Monitors reversed"
date: 2008-11-03
forum: Multimedia Software
---

### Post by dracomias on 2008-11-03
Hi,
Sorry in advance if I am not providing sufficient information in regards to my problem, what happened is I had installed Ubuntu (previous version, not the newest one) and found I was able to get my dual monitors up and running AOK, but they were reversed with the mouse, so to get to the second monotir instead of going to the right and onto the 2nd screen as usual I had to go to the far left and then it would appear...is there a fix for this or an option to select, I am going to be installing the latest ver of Ubuntu and wanted to tackle this right away.
Draco

---

### Post by fenian on 2008-11-03
You need to edit the xorg.conf file,open a terminal and enter....

> sudo gedit /etc/X11/xorg.conf

Inthe file that opens find the section that looks like this...

> Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

In the line where it says 

 "Screen1" RightOf "Screen0" 

Change "RighOf" to "LeftOf"  (If it says "LeftOf" to begin with change it to "RightOf")

---

### Post by fenian on 2008-11-03
oops double post

---

### Post by dracomias on 2008-11-03
Thank you, sounds like that is the fix
Draco

---

