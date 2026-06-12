---
title: "[SOLVED]  How to switch default apps"
date: 2020-05-11
forum: Multimedia Software
---

### Post by jarp53 on 2020-05-11
solvesI want to switch from fxce4-screenshooter to GNOME Screenshot , as my default app when I press PrtScn key, the fxce 0ne has a dialogue box, while the gnome one is automatic , at least it used to be when I used it in ubuntu 1804 ; I try removing from Software but it does not work and I'm thinking is because is a default package , I know I can probably install Sypnatic, or even < sudo apt-get remove fxce4-screeshooter > ( if that's the correct command ). but I just think is best to ask if , first : is gnome going to work , and am I going to break any thing if I do switch .

---

### Post by &amp;KyT$0P# on 2020-05-11
> **jarp53 said:**
> is gnome going to work , 

I don't understand this question.  Just install GNOME Screenshot, without "switching" anything or removing anything, and try it out and see if it works for you?

---

### Post by Yellow Pasque on 2020-05-11
You can change the behavior in the Keyboard settings ('Application Shortcuts'). So you can install gnome-screenshot and set the PrintScreen key to run that.

You can also make xfce4-screenshooter automatic if you give it the options you want to use:
```
xfce4-screenshooter -w -d 0 -s ~/Pictures/filename.png
```
[https://docs.xfce.org/apps/screenshooter/4.14/usage#via_command-line](https://docs.xfce.org/apps/screenshooter/4.14/usage#via_command-line)

---

### Post by jarp53 on 2020-05-11
thanks ; I  try the command line but it still show the box so I switch the application shortcut and that works

---

