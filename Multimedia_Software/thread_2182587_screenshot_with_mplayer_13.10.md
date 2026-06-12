---
title: "screenshot with mplayer 13.10"
date: 2013-10-21
forum: Multimedia Software
---

### Post by shantiq on 2013-10-21
if i ran this in 13.04 it worked a dream   screenshots ended up in the folder where the video was    simply by pressing  the s key


```
mplayer -fs -playlist file.m3u
```


now in 13.10 at this point it gives me this

```
sending VFCTRL_SCREENSHOT!
failed (forgot -vf screenshot?)
A:3100.3 V:3100.3 A-V:  0.001 ct: -0.011   0/  0 49% 13%  1.0% 7 0 
sending VFCTRL_SCREENSHOT!
failed (forgot -vf screenshot?)
A:3100.5 V:3100.5 A-V:  0.000 ct: -0.011   0/  0 49% 13%  1.0% 7 0 
sending VFCTRL_SCREENSHOT!
failed (forgot -vf screenshot?)
A:3100.7 V:3100.7 A-V:  0.000 ct: -0.011   0/  0 49% 13%  1.0% 7 0 
sending VFCTRL_SCREENSHOT!
failed (forgot -vf screenshot?)
A:3100.9 V:3100.9 A-V:  0.000 ct: -0.011   0/  0 49% 13%  1.0% 7 0 

```


any suggestions?  

my version of mplayer is   MPlayer SVN-r36481-4.8 (C) 2000-2013 MPlayer Team

---

### Post by mc4man on 2013-10-22
Well, take it's advice & add this to your command
```
-vf screenshot
```
or add to your ~/.mplayer/config

vf=screenshot

---

### Post by shantiq on 2013-10-22
Hi there Doug   thanx for reply

there is nothing in that config document

so i added  vf=screenshot   and badaboom    all good!      thanx Doug
i really did not understand what was meant by forgot -vf screenshot


i never had had to add this before...    wonder why?    anyway absolutely useful a function

---

