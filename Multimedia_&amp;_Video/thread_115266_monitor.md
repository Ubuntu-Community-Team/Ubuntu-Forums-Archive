---
title: "monitor"
date: 2006-01-10
forum: Multimedia &amp; Video
---

### Post by krisklash on 2006-01-10
hello all. i have just installed UBUNTU 5.10
my problem is that the OS starts good and seems to load everything but my monitor shows (OUT OF RANGE H: 1khz  V:194.5hz) and locks up?

---

### Post by lisje on 2006-01-10
Could you tell us what's inside your xorg.conf (/etc/X11/xorg.conf) and what monitor you have?
thx,
Lisje

---

### Post by krisklash on 2006-01-12
my monitor is a Standard plug & play CTR. on a S3 Trio32/64 Card. 
i cant see the ubuntu partition from windows so I dont know what's inside my xorg.conf file!!!!

---

### Post by h3avyarms on 2006-01-12
You should be able to press Ctl+Alt+F1 to switch to the console there you can login and look at your xorg.conf and make changes.

---

### Post by krisklash on 2006-01-12
[QUOTE=h3avyarms]You should be able to press Ctl+Alt+F1 to switch to the console there you can login and look at your xorg.conf and make changes.[/QUOTE]


I cant see anything when OS finish loads just the monitor message (OUT OF RANGE H: 1khz V:194.5hz)can i edit xorg.conf in windows?

i can boot into UBUNTU recovery mode will that help?

---

### Post by krisklash on 2006-01-13
Quote:
Originally Posted by h3avyarms
You should be able to press Ctl+Alt+F1 to switch to the console there you can login and look at your xorg.conf and make changes.


I cant see anything when OS finish loads just the monitor message (OUT OF RANGE H: 1khz V:194.5hz)can i edit xorg.conf in windows?

i can boot into UBUNTU recovery mode will that help?

---

### Post by camus on 2006-01-13
I'm having the same problem with a viewsonic lcd 17" a got a couple weeks ago. Runs fine on windows partition, but I can't see the gui. Anyway, I've been trying to get to my xorg.conf and mess with it (as this thread and others have suggested), but I haven't used linux in awhile (since some classes for my major) and I can't remember the commands to get to it. Any help is appreciated, I pretty much know what needs to be done, I just don't know how to do it in linux.

---

### Post by lisje on 2006-01-15
You could do: 
When your ubuntu has finished booting you get the error message on your screen and then you should press ctrl+alt+f2 or f1 like h3avyarms has suggested.
Then you'll be taken to a commandline interface (like dos). You just log into it, using your normal login.

1. From there you can edit your xorg.conf like this:
```
sudo vim /etc/X11/xorg.conf
```
vim is an commandline editor (choose the one you like)

2. but maybe, it should be easier if you just reconfigured xorg/xserver by doing this (from the commandline where you should have logged into):
```
sudo dpkg-reconfigure xserver-xorg
```
I suggest you try this first.

when reconfiguration fails, then try to edit your xorg.conf or copy it to a medium that you can use in windows (a fat partition or a usb-pen, ...) so you can post it here.

on how to use commandline you should look up info about bash.. Don't hesistate to ask questions.
If you're system really locks up and pressing alt+ctl+f1 or alt+ctl+f2 doesn't result in being taken to a commandline interface you should try booting a live-cd or something... ask for more info if my other solutions fail.

greets,
Lisje

---

### Post by krisklash on 2006-01-19
[

2. but maybe, it should be easier if you just reconfigured xorg/xserver by doing this (from the commandline where you should have logged into):
```
sudo dpkg-reconfigure xserver-xorg
```
I suggest you try this first.

thank you i used the above and it worked!!!!!:D 

thanks again to lisje, & h3avyarms, i just have to fine out how to configer unbuntu for me now!

---

